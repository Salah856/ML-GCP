

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
