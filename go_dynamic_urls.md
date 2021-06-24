

You see a lot of stories on medium about how to do complex tasks or architect a production-level project. What you don’t see enough is how to do something as simple as building URLs with Golang, a task almost every micro-service does, however, nobody has a good way to do it. 


In this tutorial, we will walk through how to build URLs cleanly, config-driven, and best of all, testable

First, we are going to define our struct, the struct will be our basis for building config-driven URLs. Almost every REST URL is made up of static (host, schema, etc) and dynamic parts (query and route parameters). The struct will host all of our static parts derived from the application configuration.

We will give the struct default values, but in a real-world application, I would recommend populating the struct through a config file.

```go

package main

import (
	"log"
)

type endpoint struct {
	Path string `yaml:"path"`
	Method string `yaml:"method"`
}

type weatherAPI struct {
	Scheme string `yaml:"scheme"`
	Host string `yaml:"host"`
	Endpoints weatherEndpoints `yaml:"endpoints"`
}

type weatherEndpoints struct {
	Forecast endpoint `yaml:"forecast"`
	Sports endpoint `yaml:"sports"`
}

func main() {
	conn := weatherAPI{
		Scheme:    "https",
		Host:      "api.weatherapi.com/v1",
		Endpoints: weatherEndpoints{
			Forecast: endpoint{
				Path:   "/forecast.json",
				Method: "GET",
			},
			Sports: endpoint{
				Path:   "/sports.json",
				Method: "GET",
			},
		},
	}
	
	log.Println(conn)
}

```


Second, let’s define our first dynamic endpoint and than break it down piece by piece to make sure we truly understand it.

```go

type Formatter func() (string, *url.URL)

func (w *weatherAPI) ForecastURL(date, region string) Formatter {
	return func() (string, *url.URL) {
		u := &url.URL{
			Scheme:      w.Scheme,
			Host:        w.Host,
			Path: 	     w.Endpoints.Forecast.Path,
		}

		rq := u.Query()

		rq.Set("dateKey", date)
		rq.Set("regionKey", region)

		u.RawQuery = rq.Encode()

		return http.MethodGet, u
	}
}

```

At the top, we have our Formatter return type, which is basically just defining what our method receiver will return. A string for the HTTP method, and the Golang built-in type url.URL as the second.

Next, we are creating our base url.URL object with the values held in the struct, since this is a go method receiver. These should be the config-driven static values that you add to that specific URL.

Below the static values, we are adding the dynamic query parameters to the URL, which we encode and assign.

Let’s take a look at our main.go integration with our new URL building receiver.

```go

func main() {
	conn := weatherAPI{
		Scheme:    "https",
		Host:      "api.weatherapi.com",
		Endpoints: weatherEndpoints{
			Forecast: endpoint{
				Path:   "/forecast.json",
				Method: "GET",
			},
			Sports: endpoint{
				Path:   "/sports.json",
				Method: "GET",
			},
		},
	}

	f := conn.ForecastURL("testDate", "testRegion")

	m, u := f()

	log.Println(m)
	log.Println(u)
}

```


```bash
go run main.go

  2021/06/22 22:36:51 GET
  
  2021/06/22 22:36:51 https://api.weatherapi.com/forecast.json?dateKey=testDate&regionKey=testRegion


```

## References

<a href="https://noahkreiger.medium.com/golang-building-dynamic-urls-4e93cab86e72"> Dynamic Urls with Go  </a>
