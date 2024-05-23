# Book Library API

## Overview

The Book Library API is a simple RESTful API built with ASP.NET Core and Entity Framework Core. It allows users to perform CRUD (Create, Read, Update, Delete) operations on a collection of books. The API uses SQLite for data storage.

## Features

- Add a new book to the library
- Retrieve a list of all books
- Get details of a specific book by ID
- Update a book's information
- Delete a book from the library

## Technologies Used

- ASP.NET Core
- Entity Framework Core
- SQLite
- Swagger for API documentation

## Prerequisites

- .NET 6 SDK or later
- Entity Framework Core tools

## Getting Started

### Clone the Repository

```bash
git clone https://github.com/yourusername/BookLibraryAPI.git
cd BookLibraryAPI
```

### Install Dependencies

Ensure you have the necessary .NET tools installed:

```bash
dotnet tool install --global dotnet-ef
dotnet restore
```

### Update the Database

Run the following commands to create and apply the initial migration:

```bash
dotnet ef migrations add InitialCreate
dotnet ef database update
```

### Running the Application

Start the application using the following command:

```bash
dotnet run
```

The API will be available at `https://localhost:5001` (or the port specified in your configuration).

## API Endpoints

### Get All Books

- **URL:** `GET /api/Books`
- **Response:** A list of all books

### Get a Book by ID

- **URL:** `GET /api/Books/{id}`
- **Response:** The book with the specified ID

### Add a New Book

- **URL:** `POST /api/Books`
- **Request Body:**
  ```json
  {
    "title": "The Great Gatsby",
    "author": "F. Scott Fitzgerald",
    "isbn": "9780743273565",
    "publishedYear": 1925
  }
  ```

### Update a Book

- **URL:** `PUT /api/Books/{id}`
- **Request Body:**
  ```json
  {
    "id": 1,
    "title": "The Great Gatsby",
    "author": "F. Scott Fitzgerald",
    "isbn": "9780743273565",
    "publishedYear": 1925
  }
  ```

### Delete a Book

- **URL:** `DELETE /api/Books/{id}`

## Using Swagger

Swagger is integrated for API documentation. Once the application is running, navigate to `https://localhost:5001/swagger` to view and interact with the API endpoints.

## Example Requests

### Using `curl`

#### Add a Book

```bash
curl -X POST https://localhost:5001/api/Books \
-H "Content-Type: application/json" \
-d '{
      "title": "The Great Gatsby",
      "author": "F. Scott Fitzgerald",
      "isbn": "9780743273565",
      "publishedYear": 1925
    }'
```

#### Get All Books

```bash
curl https://localhost:5001/api/Books
```

### Using Postman

1. Open Postman.
2. Create a new request.
3. Set the request type to POST and the URL to `https://localhost:5001/api/Books`.
4. Set the request body to raw and select JSON format.
5. Enter the JSON data for the new book.
6. Send the request.
