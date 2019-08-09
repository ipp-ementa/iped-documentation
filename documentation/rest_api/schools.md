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
        "id":"1",
        "acronym":"ISEP"
        "name":"Instituto Superior de Engenharia do Porto"
    },
    {
        "id":"2",
        "acronym":"ESMAD"
        "name":"Escola Superior de Media Artes e Design"
    }
]

```

### Error Responses

`404` - No schools are available

`500` - The server failed to resolve the request


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
            "name":"Cantina do H"
        },
        {
            "name":"Bar da AE"
        },
        {
            "name":"Cantina do F"
        }
    ]
}

```

### Success Responses

`201 Created` - The school was successfully created, adding a resource to schools collection

Example:

```

{
    "id":"1",
    "acronym":"ISEP",
    "name":"Instituto Superior de Engenharia do Porto",
    "canteens":[
        {
            "name":"Cantina do H"
        },
        {
            "name":"Bar da AE"
        },
        {
            "name":"Cantina do F"
        }
    ]
}

```

### Error Responses

`400` - An error occurred while creating the school due to an invalid field

Example:

```

{
    "message":"The school already exists"
}

```

`500` - The server failed to resolve the request


## Detailed school information

Retrieves detailed information about a school using its resource identifier.

URI: `/schools/:id`

Verb: `GET`

### Success Responses

`200 OK` - The school was found

Example:

```

{
    "id":"1",
    "acronym":"ISEP",
    "name":"Instituto Superior de Engenharia do Porto",
    "canteens":[
        {
            "name":"Cantina do H"
        },
        {
            "name":"Bar da AE"
        },
        {
            "name":"Cantina do F"
        }
    ]
}

```

### Error Responses

`404` - No school with the specified resource identifier was found

`500` - The server failed to resolve the request