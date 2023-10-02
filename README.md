# Microservice Overview

## Netflix Eureka Discovery Service

The Discovery Service serves as a service registry and allowing microservices to discover and communicate with each other dynamically.

reference: https://github.com/YuraVoitovich/modsen-task-discovery-server


## Spring Cloud Gateway 
The Gateway Service is responsible for managing all incoming requests and directing them to the appropriate microservices.

reference: https://github.com/YuraVoitovich/modsen-task-gateway

## Config Server 

Config Server is a microservice that provides centralized configuration management for your application ecosystem.

reference: https://github.com/YuraVoitovich/modsen-task-config-server

## Book Service

Book Service is a microservice that manages information related to books in your application ecosystem. It plays a crucial role in handling book-related data.

reference: https://github.com/YuraVoitovich/book-service

## Library Service 

Library Service is a microservice designed to manage the borrowing and return of books within your application ecosystem. It plays a crucial role in keeping track of when books are borrowed and their expected return dates.

reference: https://github.com/YuraVoitovich/library-service


# API Reference

### Get all books

```http
  GET /book-service/books
```
#### Description: 
Retrieve a list of all available books in the library.
#### Authentication: 
Requires authentication with 'modsen-user' role.

### Get book by id

```http
  GET /book-service/book/${id}
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `id`      | `UUID` | **Required**. Id of book to fetch |

#### Description: 
Retrieve detailed information about a book by its unique identifier (UUID).
#### Authentication: 
Requires authentication with 'modsen-user' role.


### Get book by isbn

```http
  GET /book-service/book-isbn/${isbn}
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `isbn`      | `String` | **Required**. isbn of book to fetch |

#### Description: 
Retrieve a book by its ISBN (International Standard Book Number).
#### Authentication: 
Requires authentication with 'modsen-user' role.

### Add book

```http
  PUT /book-service/book
```

| Body | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `Book DTO`      | `BookDTO` | **Required**. Book information |

#### Description: 
Add a new book to the library.
#### Authentication: 
Requires authentication with 'modsen-admin' role.

### Update book

```http
  POST /book-service/book
```

| Body | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `Book DTO`      | `BookDTO` | **Required**. Book information |

#### Description: 
Update an existing book's details. 

#### Authentication: 
Requires authentication with 'modsen-admin' role.


### Delete book

```http
  DELETE /book-service/book/{id}
```

| Body | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `id`      | `UUID` | **Required**. Id of book to delete |

#### Description: 
Remove a book from the library by its unique identifier (ID).

#### Authentication: 
Requires authentication with 'modsen-admin' role.

### Take book

```http
  POST /book-service/book/{id}
```

| Body | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `id`      | `UUID` | **Required**. Id of book to take |

#### Description: 
Mark a book as taken, recording the borrowing date.

#### Authentication: 
Requires authentication with 'modsen-user' role.




# Authetication 
Most endpoints require authentication with specific roles ('modsen-user' or 'modsen-admin') to access the functionality. Ensure proper user roles are assigned for each endpoint to maintain security and access control.
# Booting 

You should run 
```code
  git clone "project path".
```
to clone all nessary mecroservices.

Then you should run maven instruction to build a .jar file for all related microservices:

```code
  mvn clean package
```

Then you should buid docker images for all microservices, running docker command: 


```code
  docker build -t "image name" "Dockerfile path"
```
You should use image names that are described in the docker-compose.yml, or use your names and change docker images names in the docker-compose.yml

Then you should run: 

```code
  docker-compose up
```


