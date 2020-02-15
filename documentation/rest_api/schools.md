# About

This document presents information regarding `schools` collection functionalities

## Available schools

Retrieves available schools as an array.

URI: `/schools`

Verb: `GET`

### Success Responses

`200 OK` - One or more schools have been retrieved

Example:

```

[
    {
        "id":1,
        "acronym":"ISEP",
        "name":"Instituto Superior de Engenharia do Porto"
    },
    {
        "id":2,
        "acronym":"ESMAD",
        "name":"Escola Superior de Media Artes e Design"
    }
]

```

### Error Responses

`404 Not Found` - No schools are available

`500 Internal Server Error` - The server failed to resolve the request


## Create a new school

Allows the creation of a new school.

URI: `/schools`

Verb: `POST`

### Required data

The following fields are required in order to create a school:

- `acronym` The school unique identifier
- `name` Full name of the school
- `canteens` An array of the school canteens

Example:

```

{
    "acronym":"ISEP",
    "name":"Instituto Superior de Engenharia do Porto",
    "canteens":[
        {
            "name":"Cantina do H",
            "location":{
                "latitude": 41.177965,
                "longitude": -8.608679
            }
        },
        {
            "name":"Bar da AE",
            "location":{
                "latitude": 41.177965,
                "longitude": -8.608679
            }
        },
        {
            "name":"Cantina do F",
            "location":{
                "latitude": 41.178266,
                "longitude": -8.608284
            }
        }
    ]
}

```

### Success Responses

`201 Created` - The school was successfully created, adding a resource to schools collection

Example:

```

{
    "id":1,
    "acronym":"ISEP",
    "name":"Instituto Superior de Engenharia do Porto",
    "canteens":[
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
}

```

### Error Responses

`400 Bad Request` - An error occurred while creating the school due to an invalid field

Example:

```

{
    "message":"The school already exists"
}

```

`401 Unauthorized` - The authorization key was denied

`500 Internal Server Error` - The server failed to resolve the request


## Detailed school information

Retrieves detailed information of a school using its resource identifier.

URI: `/schools/:id`

Verb: `GET`

### Success Responses

`200 OK` - The school was found

Example:

```

{
    "id":1,
    "acronym":"ISEP",
    "name":"Instituto Superior de Engenharia do Porto",
    "canteens":[
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
}

```

### Error Responses

`404 Not Found` - No school with the specified resource identifier was found

`500 Internal Server Error` - The server failed to resolve the request