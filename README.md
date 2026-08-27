\# Swagger Petstore API Documentation



The Swagger Petstore is a sample API used for learning and practicing how RESTful APIs work. This document covers three key endpoints:



\- `GET /pet/findByStatus` — fetch pets by status

\- `POST /pet` — add a new pet

\- `GET /pet/{petId}` — fetch one specific pet by ID



\## Get Pets by Status



\*\*Method:\*\* `GET`



\*\*Path:\*\* `/pet/findByStatus`



This endpoint returns a list of pets filtered by their status. Each pet in the response includes its full details, such as `id`, `name`, and `category`.



\*\*Parameters:\*\*

\- `status` (required) — filters pets by their current status. Accepted values: `available`, `pending`, `sold`



\*\*Possible responses:\*\*

\- `200 OK` — request succeeded, returns a list of matching pets

\- `400 Bad Request` — invalid status value provided



\## Add a New Pet



\*\*Method:\*\* `POST`



\*\*Path:\*\* `/pet`



This endpoint adds a new pet to the store. To create a pet, send its details in the request body, including `id`, `name`, `category`, and `status`.



\*\*Request body example:\*\*



```json

{

&#x20; "id": 1,

&#x20; "name": "Buddy",

&#x20; "category": {

&#x20;   "id": 1,

&#x20;   "name": "Dogs"

&#x20; },

&#x20; "status": "available"

}

```



\*\*Possible responses:\*\*

\- `201 Created` — the new pet was successfully added

\- `422 Unprocessable Entity` — the request was understood, but some field values were invalid (e.g. `id` sent as text instead of a number)



\## Get Pet by ID



\*\*Method:\*\* `GET`



\*\*Path:\*\* `/pet/{petId}`



This endpoint returns the details of one specific pet, identified by its ID. The response includes the pet's full details, such as `id`, `name`, and `category`.



\*\*Parameters:\*\*

\- `petId` (required, path parameter) — the ID of the pet to retrieve



\*\*Possible responses:\*\*

\- `200 OK` — pet found, returns pet details

\- `404 Not Found` — no pet exists with the given ID



\## About This Documentation



This documentation was created as a practice project to demonstrate API documentation skills, covering the Swagger Petstore's `pet` endpoints. It includes endpoint descriptions, request/response examples, and possible status codes for each operation.

