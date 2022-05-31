# REST-API-GENERATOR
[![](https://img.shields.io/badge/pypi-v1.0.0-blue)](https://pypi.org/project/REST-API-Generator/)  
![](https://img.shields.io/badge/python-v3.6%7Cv3.7%7Cv3.8%7Cv3.9-brightgreen)

**REST-API-GENERATOR** is a python tool that helps reduce the time it takes to create dummy REST endpoints during the initial stages of your project.

## Installation
` pip install REST-API-Generator `

## Supported Frameworks
>1. Sanic

## How to use it

To use **REST-API-GENERATOR** package to create dummy REST endpoints you have to provide a `python dict` as an input. This `python dict` shall contain all the necessary information of the REST endpoints that you want to build.  

#### *Take a look at the sample input json file below*

```
{  
    "project_dir": "~/project_dir",  
    "project_name": "Test_project",  
    "framekwork": "sanic",  
    "host": "0.0.0.0",  
    "port": "1201",  
    "api_list": [ 
        {  
            "method_handler_name": "get_name",  
            "HTTP_method": "GET",  
            "path": "/name",  
            "response": [  
                "name1",  
                "name2"  
            ]  
        },  
        {  
            "method_handler_name": "add_name",  
            "HTTP_method": "POST",  
            "path": "/add_name",  
            "response": "new_name"  
        },  
        {  
            "method_handler_name": "update_name",  
            "HTTP_method": "PUT",  
            "path": "/update_name",  
            "response": "name3"  
        }
    ]  
}  
```
```
project_dir  : root directory path of the intended project
project_name : name of the project
framekwork   : name of the framework in which the project is created
host         : host address of the server
port         : port address of the server

api_list     : list of all the individual end points
    method_handler_name : name of a method handler of a particular end-point
    HTTP_method         : HTTP method type
    path                : url path
    response            : sample response
```


` Use the following python script to generate dummy end-points `

#### - ***Sanic framework***
```
from API_Gen import SanicGenerator
import json

if __name__ == '__main__':
    with open('input.json') as file:
        api_info = json.load(file)
    sp = SanicGenerator(api_info=api_info)
    sp.create_apis()
```



