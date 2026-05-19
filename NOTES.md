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