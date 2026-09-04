# Swagger Petstore API Documentation

The Swagger Petstore is a sample API used for learning and practicing how RESTful APIs work. This document covers three key endpoints:

- `GET /pet/findByStatus` — fetch pets by status
- `POST /pet` — add a new pet
- `GET /pet/{petId}` — fetch one specific pet by ID
- `PUT /pet` - update the details of a pet
- `DELETE /pet/{petId}` - delete a pet

## Get Pets by Status

**Method:** `GET`

**Path:** `/pet/findByStatus`

This endpoint returns a list of pets filtered by their status. Each pet in the response includes its full details, such as `id`, `name`, and `category`.

**Parameters:**
- `status` (required) — filters pets by their current status. Accepted values: `available`, `pending`, `sold`

**Possible responses:**
- `200 OK` — request succeeded, returns a list of matching pets
- `400 Bad Request` — invalid status value provided

## Add a New Pet

**Method:** `POST`

**Path:** `/pet`

This endpoint adds a new pet to the store. To create a pet, send its details in the request body, including `id`, `name`, `category`, and `status`.

**Request body example:**
```json
{
  "id": 1,
  "name": "Buddy",
  "category": {
    "id": 1,
    "name": "Dogs"
  },
  "status": "available"
}
```
**Possible responses:**
- `201 Created` — the new pet was successfully added
- `422 Unprocessable Entity` — the request was understood, but some field values were invalid (e.g. `id` sent as text instead of a number)


## Update a Pet

**Method:** `PUT`

**Path:** `/pet`

This endpoint updates an existing pet's details. Since PUT replaces the entire pet object, the request body must include the pet's existing `id`, along with all its updated fields.

**Request body example:**

{
  "id": 1,
  "name": "Buddy",
  "category": {
    "id": 1,
    "name": "Dogs"
  },
  "status": "sold"
}

**Possible responses:**
- `200 OK` — pet updated successfully
- `404 Not Found` — no pet exists with the given ID

## Get Pet by ID

**Method:** `GET`

**Path:** `/pet/{petId}`

This endpoint returns the details of one specific pet, identified by its ID. The response includes the pet's full details, such as `id`, `name`, and `category`.

**Parameters:**
- `petId` (required, path parameter) — the ID of the pet to retrieve

**Possible responses:**
- `200 OK` — pet found, returns pet details
- `404 Not Found` — no pet exists with the given ID

## Delete a Pet by ID

**Method:** `DELETE`

**Path:** `/pet/{petId}`

This endpoint deletes the pet with the specific ID. The response body is empty after successful deletion.

**Parameters:**
- `petId` (required, path parameter) — the ID of the pet to retrieve

**Possible responses:**
- `200 OK` — pet deleted
- `404 Not Found` — no pet exists with the given ID

## Get Pet Inventory

**Method:** `GET`

**Path:** `/store/inventory`

This endpoint returns a summary of pet counts, grouped by their current status (available, pending, or sold).

**Response body example:**

{
  "available": 12,
  "pending": 3,
  "sold": 5
}

**Possible responses:**
- `200 OK` — inventory summary returned successfully

## Place an order

**Method:** `POST`

**Path:** `/store/order`

This endpoint creates a new order for a pet, recording details like which pet was ordered, the quantity, and the shipping date.

**Request body example:**

{
  "id": 1,
  "petId": 10,
  "quantity": 1,
  "shipDate": "2026-10-11",
  "status": "placed",
  "complete": false
}

**Possible responses:**
- `201 Created` — order placed successfully
- `400 Bad Request` — invalid order details provided

## Get Order by ID

**Method:** `GET`

**Path:** `/store/order/{orderId}`

This endpoint returns the details of a specific order, including its quantity, shipping date, status, and whether it's complete.

**Parameters:**
- `orderId` (required, path parameter) — the ID of the order to retrieve

**Response body example:**

{
  "id": 1,
  "petId": 10,
  "quantity": 1,
  "shipDate": "2026-10-11",
  "status": "placed",
  "complete": false
}

**Possible responses:**
- `200 OK` — order found
- `404 Not Found` — no order exists with the given ID

## Delete an Order by ID

**Method:** `DELETE`

**Path:** `/store/order/{orderId}`

This endpoint deletes the order with the specified ID. The response body is empty after a successful deletion.

**Parameters:**
- `orderId` (required, path parameter) — the ID of the order to delete

**Possible responses:**
- `200 OK` — order deleted
- `404 Not Found` — no order exists with the given ID

## Create a User

**Method:** `POST`

**Path:** `/user`

This endpoint creates a new user account, recording details like username, name, email, password, phone number, and account status.

**Request body example:**

{
  "id": 1,
  "username": "laila1",
  "firstName": "Laila",
  "lastName": "Rills",
  "email": "laila@example.com",
  "password": "password123",
  "phone": "9876543210",
  "userStatus": 1
}

**Possible responses:**
- `201 Created` — user created successfully
- `400 Bad Request` — invalid details provided

## Create Multiple Users

**Method:** `POST`

**Path:** `/user/createWithList`

This endpoint creates multiple user accounts in a single request. Instead of calling `POST /user` repeatedly for each user, the request body accepts an array of user objects.

**Request body example:**

[
  {
    "id": 1,
    "username": "laila1",
    "firstName": "Laila",
    "lastName": "Rills",
    "email": "laila@example.com",
    "password": "password123",
    "phone": "9876543210",
    "userStatus": 1
  },
  {
    "id": 2,
    "username": "arjun2",
    "firstName": "Arjun",
    "lastName": "Mehta",
    "email": "arjun@example.com",
    "password": "password123",
    "phone": "9876543211",
    "userStatus": 1
  },
  {
    "id": 3,
    "username": "priya3",
    "firstName": "Priya",
    "lastName": "Shah",
    "email": "priya@example.com",
    "password": "password123",
    "phone": "9876543212",
    "userStatus": 1
  }
]

**Possible responses:**
- `201 Created` — users created successfully
- `400 Bad Request` — invalid details provided

## Get User by Username

**Method:** `GET`

**Path:** `/user/{username}`

This endpoint returns the details of a user, identified by their username. The response includes details like `id`, `firstName`, `lastName`, `email`, `password`, `phone`, and `userStatus`.

**Parameters:**
- `username` (required, path parameter) — the username of the user to retrieve

**Response body example:**
{
  "id": 3,
  "username": "priya3",
  "firstName": "Priya",
  "lastName": "Shah",
  "email": "priya@example.com",
  "password": "password123",
  "phone": "9876543212",
  "userStatus": 1
}

**Possible responses:**
- `200 OK` — user found
- `404 Not Found` — no user exists with the given username

## Update a User

**Method:** `PUT`

**Path:** `/user/{username}`

This endpoint updates an existing user's details. The username in the path identifies which user to update, and the request body should include all the user's updated fields.

**Parameters:**
- `username` (required, path parameter) — the username of the user to update

**Request body example:**

{
  "id": 3,
  "username": "priya3",
  "firstName": "Priya",
  "lastName": "Shah",
  "email": "priya@example.com",
  "password": "password123",
  "phone": "9876543212",
  "userStatus": 1
}

**Possible responses:**
- `200 OK` — user updated successfully
- `404 Not Found` — no user exists with the given username

## Delete a user

**Method:** `DELETE`

**Path:** `/user/{username}`

This endpoint deletes the user with the specified username. The response body is empty after a successful deletion.

**Parameters:**
- `username` (required, path parameter) — the username of the user to delete

**Possible responses:**
- `200 OK` — user deleted
- `404 Not Found` — no user exists with the given username

## Log In a User

**Method:** `GET`

**Path:** `/user/login`

This endpoint logs in a user by verifying their username and password, sent as query parameters. On success, it returns a session token.

**Parameters:**
- `username` (required, query parameter) — the user's username
- `password` (required, query parameter) — the user's password

**Response body example:**

{
  "token": "abc123xyz"
}

**Possible responses:**
- `200 OK` — login successful, returns a session token
- `400 Bad Request` — invalid username or password

## Log Out a User

**Method:** `GET`

**Path:** `/user/logout`

This endpoint logs out the currently logged-in user. No parameters are required.

**Response body example:**

{
  "message": "User logged out successfully"
}

**Possible responses:**
- `200 OK` — user logged out successfully
- `400 Bad Request` — unexpected error

## About This Documentation

This documentation was created as a practice project to demonstrate API documentation skills, covering the Swagger Petstore's `pet` endpoints. It includes endpoint descriptions, request/response examples, and possible status codes for each operation.
