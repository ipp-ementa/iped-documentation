# About

This document presents information regarding `dishes` collection functionalities.
Dishes belong to a school canteen menu, so the collection functionalities are only available after selecting a school canteen menu.

Base URI: `schools/:id/canteens/:id/menus/:id`

## Available dishes

Retrieves available dishes as an array.

URI: `/dishes`

Verb: `GET`

### Success Responses

`200 OK` - One or more dishes have been retrieved

Example:

```

[
    {
        "id":1,
        "type":"meat",
        "description":"Arroz de pato"
    },
    {
        "id":2,
        "type":"vegetarian",
        "description":"Tofu com tomate"
    }
]

```

### Error Responses

`404 Not Found` - No dishes are available

`500 Internal Server Error` - The server failed to resolve the request


## Detailed dish information

Retrieves detailed information of a menu dish using its resource identifier.

URI: `/dishes/:id`

Verb: `GET`

### Success Responses

`200 OK` - The dish was found

Example:

```

{
    "id":1,
    "type":"meat",
    "description":"Arroz de pato"
}

```

### Error Responses

`404 Not Found` - No dish with the specified resource identifier was found

`500 Internal Server Error` - The server failed to resolve the request