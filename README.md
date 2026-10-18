# Movie Review API

A REST API for managing movies and their reviews, built with Java and Spring Boot and backed by MongoDB. I tested all endpoints with Postman.

## Tech Stack

- Java
- Spring Boot
- Spring Data MongoDB
- MongoDB
- Maven (with the Maven wrapper)
- Postman (for testing)

## Features

- Create, read, update, and delete movies
- Add and view reviews for a movie
- Layered structure: controller, service, and repository

## Project Structure

```
src/main/java/com/example/Movies/
├── Movie.java               # Movie document (MongoDB model)
├── Review.java              # Review document (MongoDB model)
├── MovieController.java     # Movie REST endpoints
├── ReviewController.java    # Review REST endpoints
├── MovieService.java        # Movie business logic
├── ReviewService.java       # Review business logic
├── MovieRepository.java     # Movie database access
├── ReviewRepository.java    # Review database access
└── MoviesApplication.java   # Application entry point
```

## Prerequisites

- JDK 17 or newer (check your `pom.xml` for the exact version)
- MongoDB running locally, or a MongoDB Atlas connection string
- Postman (optional, for testing)

## Configuration

Set your MongoDB connection in `src/main/resources/application.properties`:

```properties
spring.data.mongodb.uri=mongodb://localhost:27017/moviesdb
```

For a shared or public setup, do not commit real credentials. Use an environment variable instead:

```properties
spring.data.mongodb.uri=${MONGODB_URI}
```

## Running the Application

```bash
./mvnw spring-boot:run
```

On Windows, use `mvnw.cmd spring-boot:run`.

The API starts on `http://localhost:8080`.

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/movies` | Get all movies |
| GET | `/api/movies/{id}` | Get a movie by ID |
| POST | `/api/movies` | Create a movie |
| PUT | `/api/movies/{id}` | Update a movie |
| DELETE | `/api/movies/{id}` | Delete a movie |
| POST | `/api/movies/{id}/reviews` | Add a review to a movie |

Update this table with your actual paths and methods before publishing.

## Example Request

Create a movie:

```json
POST /api/movies
{
  "title": "Inception",
  "director": "Christopher Nolan",
  "year": 2010
}
```

## Testing

I tested every endpoint manually with Postman, covering successful requests and error cases such as missing or invalid IDs.

## Possible Improvements

- Add input validation with `@Valid` and Bean Validation annotations
- Return proper HTTP status codes and error messages for every failure case
- Add unit and integration tests with JUnit and Testcontainers
- Add authentication so only logged-in users can post reviews
- Calculate average ratings for each movie
