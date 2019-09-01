# About

This document presents information regarding `canteens` collection functionalities.
Canteens belong to a school, so the collection functionalities are only available after selecting a school.

Base URI: `schools/:id`

## Available canteens

Retrieves available canteens as an array.

URI: `/canteens`

Verb: `GET`

### Success Responses

`200 OK` - One or more canteens have been retrieved

Example:

```

[
    {
        "id":1,
        "name":"Cantina do H"
    },
    {
        "id":2,
        "name":"Bar da AE"
    },
    {
        "id":3,
        "name":"Cantina do F"
    }
]

```

### Error Responses

`404 Not Found` - No canteens are available

`500 Internal Server Error` - The server failed to resolve the request


## Create a new canteen

Allows the creation of a new school canteen.

URI: `/canteens`

Verb: `POST`

### Required data

The following fields are required in order to create a school canteen:

- `name` Full name of the canteen, which identifies the canteen as unique

Example:

```

{
    "name":"Cantina do H",
}

```

### Success Responses

`201 Created` - The canteen was successfully created, adding a resource to canteens collection

Example:

```

{
    "id":1,
    "name":"Cantina do H",
}

```

### Error Responses

`400 Bad Request` - An error occurred while creating the canteen due to an invalid field

Example:

```

{
    "message":"The canteen already exists"
}

```

`401 Unauthorized` - The authorization key was denied

`500 Internal Server Error` - The server failed to resolve the request


## Detailed canteen information

Retrieves detailed information of a school canteen using its resource identifier.

URI: `/canteens/:id`

Verb: `GET`

### Success Responses

`200 OK` - The canteen was found

Example:

```

{
    "id":1,
    "name":"Cantina do H"
}

```

### Error Responses

`404 Not Found` - No canteen with the specified resource identifier was found

`500 Internal Server Error` - The server failed to resolve the request