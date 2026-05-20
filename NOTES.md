# What is a REST API?

## API

API = "application programming interface"

API helps Clients communicate with the service so it can understand and fullfill the request.

## REST

Representational State Transfer

Set of guiding principles that impose conditions on how an API should work.

A REST or RESTFUL API is one that conforms to the REST architectural style.

### Resource

any object, document or thing that the API can recieve from or send to clients.

Example: Games, Songs, Users, Posts ...

#### Uniform Resource Identifier (URI)
protocol://domain/resource

```
http://example.com/games
```

### How to interact with a REST API?

In general via a Request using the URI: http://example.com/games

in Rest there are different HTTP Methods:

||||
| -------   | ------- | ------- |
|Create     |POST       |Creates a new resource|
|Read       |GET        |Retrieves the resource representation/state|
|Update     |PUT        |Updates an existing resource|
|Delete     |DELETE     |Deletes a resource|

#### HTTTP GET

Example:
```
GET /games
```
Server responds with a message containing the STATUS and the RESULT in JSON format.

```
200 OK (<- Status)
[
    {
        "id": 1, "name": "Street Fighter II"
    },
    {
        "id": 2, "name": "Astro Bot"
    }
]
```

#### HTTP POST

The client can create a resource by using POST.

```
POST /games
{
    "name": "Street Fighter II"
}
```

The server will repsond with a message confirming the creation:

```
201 Created
{
    "id": 1, "name": "Street Fighter II"
}
```

#### HTTP PUT

The client can update a resource using PUT.

```
PUT /games/1
{
    "name": "Street Fighter II Turbo"
}
```

Usually the server will reply only with a status code 

```
204 No Content
```

#### HTTTP Delete
Request:
```
DELETE /games/1
``` 
Response:
```
204 No Content
```

### Data Validation

In ASP.NET Core data validation for endpoints can be performed using data annotations.

In order to use these annotations include the namespace `System.ComponentModel.DataAnnotations`

```
using System.ComponentModel.DataAnnotations;

namespace GameStore.Api.Dtos;

public record CreateGameDto(
    [Required][StringLength(50)] string Name,
    string Genre,
    decimal Price,
    DateOnly ReleaseDate
);

```

In order for the application to apply the validation during HTTP requests, it has to be setup when building the app using the builder: 

```
var builder = WebApplication.CreateBuilder(args);

builder.Services.AddValidation();
```

### What is Object-Relational Mapping (O/RM)?

In principle Queries to a Database are written in SQL for example. The application is written in c# though. An overhead of converting C# requests to SQL queries would be required. 

O/RM fixes this by introducing mappings between OOP objects and database tables.

It is a technique for converting data between a relational database and aan object-oriented program.

OOP <--> O/RM <--> Relational Database

ASP.NET provides a O/RM framework called "Entity Framework Core".

### What is Entity Framework Core

A lightweight, extensible, open source and cross platform object-relational mapper for .NET.

REST API <--> Entity Framework Core <--> Database

Translates C# code to SQL statements and resulting data into resulting objects.

Benefits:
- no need to learn a new language
- minimal data-acces code (LINQ)
- tooling to keep C# models in sync with DB tables
- change tracking
- supports multiple database providers

