
# Library REST API Documentation

## Overview

The Library REST API allows users to manage books in a library.
The base URL is:

`https://api.example.com/books`

## 1. List All Books

- **Method:** GET
- **Path:** `/books`
- **Description:** Retrieves all books in the library.
- **Success Status:** 200 OK
- **Example Request:**
  `GET /books`

## 2. Get One Book

- **Method:** GET
- **Path:** `/books/{id}`
- **Description:** Retrieves a book using its unique ID.
- **Success Status:** 200 OK
- **Example Request:**
  `GET /books/1`

## 3. Create a Book

- **Method:** POST
- **Path:** `/books`
- **Description:** Adds a new book to the library.
- **Example Request Body:**

  ```json
  {
    "title": "Things Fall Apart",
    "author": "Chinua Achebe",
    "publishedYear": 1958
  }
  ```

- **Success Status:** 201 Created

## 4. Update a Book

- **Method:** PUT
- **Path:** `/books/{id}`
- **Description:** Updates an existing book using its ID.
- **Example Request Body:**

  ```json
  {
    "title": "Things Fall Apart",
    "author": "Chinua Achebe",
    "publishedYear": 1959
  }
  ```

- **Success Status:** 200 OK

## 5. Delete a Book

- **Method:** DELETE
- **Path:** `/books/{id}`
- **Description:** Deletes a book using its ID.
- **Example Request:**
  `DELETE /books/1`
- **Success Status:** 204 No Content

## 6. List Books by Author

- **Method:** GET
- **Path:** `/books?author={author}`
- **Description:** Retrieves books written by a specified author.
- **Example Request:**
  `GET /books?author=Chinua%20Achebe`
- **Success Status:** 200 OK

## Error Responses

### 400 Bad Request

- **Description:** The request contains invalid data.
- **Example:** Creating a book without a required title or author.
- **Example Response:**

  ```json
  {
    "error": "Title and author are required."
  }
  ```

### 404 Not Found

- **Description:** The requested book does not exist.
- **Example:** Requesting `GET /books/9999` when book 9999 is not in the library.
- **Example Response:**

  ```json
  {
    "error": "Book not found."
  }
  ```
