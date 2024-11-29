# Jokes API  

**A simple RESTful API for managing jokes.**  

This API allows you to fetch random jokes, retrieve jokes by ID or type, add new jokes, edit existing jokes, and delete jokes. It is designed for learning purposes and can be tested using tools like Postman.  

---

## Table of Contents  

- [Features](#features)  
- [Setup](#setup)  
- [Endpoints](#endpoints)  
  - [GET /random](#get-random)  
  - [GET /jokes/:id](#get-jokesid)  
  - [GET /filter](#get-filter)  
  - [POST /jokes](#post-jokes)  
  - [PUT /jokes/:id](#put-jokesid)  
  - [PATCH /jokes/:id](#patch-jokesid)  
  - [DELETE /jokes/:id](#delete-jokesid)  
  - [DELETE /all](#delete-all)  
- [Testing](#testing)  

---

## Features  

1. Fetch random jokes.  
2. Retrieve jokes by their ID.  
3. Filter jokes by their type.  
4. Add new jokes.  
5. Edit jokes entirely or partially.  
6. Delete specific jokes or all jokes with an API key.  

---

## Setup  

1. Clone this repository.  
2. Install the required dependencies:  
   ```bash
   npm install
   ```
3. Start the server:  
   ```bash
   npm start
   ```  
   The server runs on `http://localhost:3000`.

4. Use Postman or any API client to interact with the endpoints.

---

## Endpoints  

### GET `/random`  

**Fetch a random joke.**  
- **Example Request:**  
  ```http
  GET http://localhost:3000/random
  ```
- **Response:**  
  ```json
  {
    "id": 1,
    "jokeText": "Why don't scientists trust atoms? Because they make up everything.",
    "jokeType": "Science"
  }
  ```

---

### GET `/jokes/:id`  

**Retrieve a specific joke by its ID.**  
- **Example Request:**  
  ```http
  GET http://localhost:3000/jokes/2
  ```
- **Response:**  
  ```json
  {
    "id": 2,
    "jokeText": "Why did the scarecrow win an award? Because he was outstanding in his field.",
    "jokeType": "Puns"
  }
  ```

---

### GET `/filter`  

**Retrieve jokes by type.**  
- **Query Parameters:**  
  - `type`: Filter by joke type (e.g., "Science", "Puns", "Wordplay", "Food", "Sports", "Movies", "Math").  
- **Example Request:**  
  ```http
  GET http://localhost:3000/filter?type=Science
  ```
- **Response:**  
  ```json
  [
    {
      "id": 1,
      "jokeText": "Why don't scientists trust atoms? Because they make up everything.",
      "jokeType": "Science"
    }
  ]
  ```

---

### POST `/jokes`  

**Add a new joke.**  
- **Request Body:**  
  ```json
  {
    "text": "What's a computer's favorite snack? Microchips.",
    "type": "Tech"
  }
  ```
- **Example Request:**  
  ```http
  POST http://localhost:3000/jokes
  ```
- **Response:**  
  ```json
  {
    "message": "Joke added successfully!",
    "joke": {
      "id": 101,
      "jokeText": "What's a computer's favorite snack? Microchips.",
      "jokeType": "Tech"
    }
  }
  ```

---

### PUT `/jokes/:id`  

**Replace an existing joke.**  
- **Request Body:**  
  ```json
  {
    "text": "Why don't programmers like nature? It has too many bugs.",
    "type": "Tech"
  }
  ```
- **Example Request:**  
  ```http
  PUT http://localhost:3000/jokes/2
  ```
- **Response:**  
  ```json
  {
    "id": 2,
    "jokeText": "Why don't programmers like nature? It has too many bugs.",
    "jokeType": "Tech"
  }
  ```

---

### PATCH `/jokes/:id`  

**Edit specific fields of a joke.**  
- **Request Body:**  
  ```json
  {
    "type": "Wordplay"
  }
  ```
- **Example Request:**  
  ```http
  PATCH http://localhost:3000/jokes/1
  ```
- **Response:**  
  ```json
  {
    "id": 1,
    "jokeText": "Why don't scientists trust atoms? Because they make up everything.",
    "jokeType": "Wordplay"
  }
  ```

---

### DELETE `/jokes/:id`  

**Delete a specific joke by ID.**  
- **Example Request:**  
  ```http
  DELETE http://localhost:3000/jokes/2
  ```
- **Response:**  
  ```http
  OK
  ```

---

### DELETE `/all`  

**Delete all jokes (requires master key).**  
- **Query Parameters:**  
  - `key`: API key for authentication.  
- **Example Request:**  
  ```http
  DELETE http://localhost:3000/all?key=4VGP2DN-6EWM4SJ-N6FGRHV-Z3PR3TT
  ```
- **Response:**  
  ```http
  OK
  ```

---

## Testing  

Use [Postman](https://www.postman.com/) or [curl](https://curl.se/) to test the API endpoints.  
- For POST, PUT, and PATCH requests, ensure to send data in the request body as JSON or URL-encoded format.  
- For DELETE `/all`, include the master key as a query parameter (`key`).
