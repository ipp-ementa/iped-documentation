# About

This document presents information regarding `menus` collection functionalities.
Menus belong to a school canteen, so the collection functionalities are only available after selecting a school canteen.

Base URI: `schools/:id/canteens/:id`

## Available menus

Retrieves available menus as an array.

URI: `/menus`

Verb: `GET`

### Success Responses

`200 OK` - One or more menus have been retrieved

Example:

```

[
    {
        "id":1,
        "type":"lunch"
    },
    {
        "id":2,
        "type":"dinner"
    }
]

```

### Error Responses

`404 Not Found` - No menus are available

`500 Internal Server Error` - The server failed to resolve the request


## Create a new menu

Allows the creation of a new menu.

URI: `/menus`

Verb: `POST`

### Required data

The following fields are required in order to create a menu:

- `type` The daily moment in which the menu is available (e.g. lunch/dinner)
- `dishes` An array of the menu dishes

Example:

```

{
    "type":"lunch",
    "dishes":[
        {
            "type":"meat",
            "description":"Arroz de pato"
        },
        {
            "type":"vegetarian",
            "description":"Tofu com tomate"
        }
    ]
}

```

### Success Responses

`201 Created` - The menu was successfully created, adding a resource to menus collection

Example:

```

{
    "id":1,
    "type":"lunch",
    "dishes":[
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
}

```

### Error Responses

`400 Bad Request` - An error occurred while creating the menu due to an invalid field

Example:

```

{
    "message":"Type 'carn' is not valid"
}

```

`401 Unauthorized` - The authorization key was denied

`500 Internal Server Error` - The server failed to resolve the request


## Detailed menu information

Retrieves detailed information of a menu using its resource identifier.

URI: `/menus/:id`

Verb: `GET`

### Success Responses

`200 OK` - The menu was found

Example:

```

{
    "id":1,
    "type":"lunch",
    "dishes":[
        {
            "id":1,
            "type":"meat",
            "description":"Arroz de pato"
        },
        {
            "id":2
            "type":"vegetarian",
            "description":"Tofu com tomate"
        }
    ]
}

```

### Error Responses

`404 Not Found` - No menu with the specified resource identifier was found

`500 Internal Server Error` - The server failed to resolve the request