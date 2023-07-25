# Go-Coffee API ☕️

<p align="center">
<img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/go/go-original-wordmark.svg" alt="GoLang" width="40" height="40"/>
<img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/docker/docker-original-wordmark.svg" alt="Docker" width="40" height="40"/>
<img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/postgresql/postgresql-original-wordmark.svg" alt="PostgreSQL" width="40" height="40"/>
<a href="https://github.com/go-chi/chi"><img src="https://cdn.rawgit.com/go-chi/chi/master/_examples/chi.svg" alt="Chi Router" width="40" height="40" /></a>
</p>

This is a simple REST API written in GoLang, designed to manage and store information about various types of coffees.

It has been developed as a learning project while diving into Golang and Docker.

## Technologies Used

-   GoLang
    -   Chi Router
    -   SQLX (including migrations)
-   Docker
-   Makefile
-   Postgres

## Choice of Technologies

The Coffee API's REST endpoints have been built using Docker, Postgres, and GoLang.

-   Docker ensures a consistent and portable environment for easy deployment across various platforms.
-   Postgres provides a reliable and efficient relational database with support for transactions and migrations.
-   GoLang offers high-performance capabilities, a standard library for HTTP handling, and the lightweight Chi Router for efficient routing.

Chi's lightweight and efficient router ensures high-performance applications, while its simplicity and flexibility make development straightforward and allow easy integration with other libraries. Notably, Chi is based on the standard library, providing a seamless and familiar experience for Golang developers.

## Project Structure

-   **cmd/server**: This directory contains the main application file (main.go), responsible for initializing the server and bootstrapping the application.
-   **controllers**: The controllers directory holds the logic for handling HTTP requests and corresponding business logic. In this case, it contains the coffee.go file, which defines functions for CRUD operations on coffee resources.
-   **db**: The db directory encapsulates the database-related code. It includes the db.go file, which handles database connections, queries, and other database-specific operations.
-   **helpers**: The helpers directory is meant for storing utility functions that can be shared across different parts of the application.
-   **migrations**: This directory contains SQL files representing database migrations. These migrations are used to set up and seed the database schema.
-   **router**: The router directory contains the router.go file, where the application's routes are defined and configured using the Chi Router.
-   **services**: The services directory houses additional service-specific logic. In this project, it contains coffee.go and response.go, which implement specific services related to coffee resources and HTTP response handling.
-   **Makefile**: The Makefile simplifies the build and installation process of the application, making it easier to set up and run the project.

## Getting Started

To run the application, you need to have Docker installed on your system.

1. Make sure you have `sqlx-cli` installed. If you haven't already, you can install it using Homebrew:

    ```bash
    brew install sqlx-cli
    ```

2. Clone the repository and navigate to the project's root directory.

3. Configure the `.env` file, starting from the `.env.example` file.

4. Build the Docker container for the database using the following command:

    ```bash
    make create_container
    ```

5. Create the database in the container using the following command:

    ```bash
    make create_db
    ```

6. Run the migrations on the database:

    ```bash
    make migrate_up
    ```

7. Once the above process is complete, you can run the application using:

    ```bash
    make run
    ``` 

## Database Migrations

Database migrations are handled using SQLX. All the SQL files required to seed the database can be found in the `migrations` folder.

## API Endpoints

The following API endpoints are available:

-   **GET /api/v1/coffees**: Retrieves a list of all stored coffees.
-   **GET /api/v1/coffees/coffee/{id}**: Retrieves details of a specific coffee by ID.
-   **POST /api/v1/coffees/coffee**: Adds a new coffee to the database.
-   **PUT /api/v1/coffees/coffee/{id}**: Updates details of a specific coffee by ID.
-   **DELETE /api/v1/coffees/coffee/{id}**: Deletes a specific coffee by ID.