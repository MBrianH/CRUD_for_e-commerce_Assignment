# E-Commerce Product Management API

A RESTful API built with Spring Boot and PostgreSQL for managing e-commerce products. This application demonstrates a clean layered architecture implementing full CRUD operations with custom search functionality.

## Project Overview

This is a backend microservice that handles product inventory management for an e-commerce platform. It provides endpoints to create, read, update, delete, and search products stored in a PostgreSQL database.

## Tech Stack

- **Java 23**
- **Spring Boot 4.0.2**
- **Spring Data JPA**
- **PostgreSQL 16.11**
- **Maven**
- **Hibernate ORM**

## Architecture

The application follows a three-tier architecture:

```
Controller Layer (REST API)
        ↓
Service Layer (Business Logic)
        ↓
Repository Layer (Data Access)
        ↓
PostgreSQL Database
```

## Database Configuration

The application connects to PostgreSQL with the following configuration:

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/ecommerce_db
spring.datasource.username=postgres
spring.datasource.password=admin
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

## Product Entity

Each product contains:
- **id**: Unique identifier (Long)
- **name**: Product name (String, unique, required)
- **description**: Product description (String)
- **price**: Product price (Double)
- **category**: Product category (String)
- **stockQuantity**: Available stock (Integer)
- **brand**: Product brand (String)

## API Endpoints

### Base URL
```
http://localhost:8080/api/products
```

### 1. Create Product
**POST** `/api/products`

**Request Body:**
```json
{
    "id": 1001,
    "name": "Wireless Bluetooth Headphones",
    "description": "Premium noise-cancelling wireless headphones with 30-hour battery life",
    "price": 89.99,
    "category": "Electronics",
    "stockQuantity": 150,
    "brand": "TechSound"
}
```

**Response:** `201 CREATED`
```json
"Product added successfully"
```

### 2. Get All Products
**GET** `/api/products`

**Response:** `200 OK`
```json
[
    {
        "id": 1001,
        "name": "Wireless Bluetooth Headphones",
        "description": "Premium noise-cancelling wireless headphones",
        "price": 89.99,
        "category": "Electronics",
        "stockQuantity": 150,
        "brand": "TechSound"
    }
]
```

### 3. Get Product by ID
**GET** `/api/products/{id}`

**Example:** `/api/products/1001`

**Response:** `200 OK`
```json
{
    "id": 1001,
    "name": "Wireless Bluetooth Headphones",
    "description": "Premium noise-cancelling wireless headphones",
    "price": 89.99,
    "category": "Electronics",
    "stockQuantity": 150,
    "brand": "TechSound"
}
```

### 4. Update Product
**PUT** `/api/products/{id}`

**Request Body:**
```json
{
    "name": "Wireless Bluetooth Headphones Pro",
    "description": "Updated premium headphones",
    "price": 99.99,
    "category": "Electronics",
    "stockQuantity": 200,
    "brand": "TechSound"
}
```

**Response:** `200 OK` (Returns updated product)

### 5. Delete Product
**DELETE** `/api/products/{id}`

**Response:** `200 OK`
```json
"Product deleted successfully"
```

### 6. Search by Price and Brand
**GET** `/api/products/search?price={price}&brand={brand}`

**Example:** `/api/products/search?price=89.99&brand=TechSound`

**Response:** `200 OK` (Returns matching products)

## Setup Instructions

### Prerequisites
- Java 23 installed
- PostgreSQL installed and running
- Maven installed

### Database Setup

1. Start PostgreSQL server
2. Create database:
```sql
CREATE DATABASE ecommerce_db;
```

### Running the Application


1. Build and run:
```bash
mvn clean install
mvn spring-boot:run
```

2. Application will start on `http://localhost:8080`

## Testing with Postman

1. Import the endpoints into Postman
2. Set request method (GET, POST, PUT, DELETE)
3. For POST/PUT requests:
   - Set header: `Content-Type: application/json`
   - Add JSON body
4. Send request and verify response

## Sample Test Data

```json
{
    "id": 1002,
    "name": "Smart Watch",
    "description": "Fitness tracking smartwatch with heart rate monitor",
    "price": 199.99,
    "category": "Electronics",
    "stockQuantity": 75,
    "brand": "FitTech"
}
```

```json
{
    "id": 1003,
    "name": "Laptop Stand",
    "description": "Ergonomic aluminum laptop stand",
    "price": 45.50,
    "category": "Accessories",
    "stockQuantity": 200,
    "brand": "DeskPro"
}
```

## What We Built

This project implements a complete REST API for product management with the following components:

- **Product Entity**: Defined the product model with all necessary fields
- **Repository Layer**: Used Spring Data JPA for database operations
- **Service Layer**: Implemented business logic including duplicate ID validation
- **Controller Layer**: Created REST endpoints for all CRUD operations
- **Custom Search**: Added functionality to search products by price and brand
- **Database Integration**: Connected Spring Boot application to PostgreSQL
- **Error Handling**: Implemented proper HTTP status codes and error messages

## Features

✅ Full CRUD operations  
✅ Input validation (duplicate ID check)  
✅ Custom search by price and brand  
✅ RESTful API design  
✅ PostgreSQL integration  
✅ Automatic table creation via Hibernate  
✅ Error handling with proper HTTP status codes  

## Error Handling

- **409 CONFLICT**: Product with ID already exists
- **404 NOT FOUND**: Product not found
- **201 CREATED**: Product successfully created
- **200 OK**: Successful operation

## Database Queries

To view data directly in PostgreSQL:

```sql
-- View all products
<img width="1123" height="546" alt="1" src="https://github.com/user-attachments/assets/789a1413-11c6-43d7-9b0a-4c07bfc691d7" />


-- View specific product
<img width="1116" height="422" alt="2" src="https://github.com/user-attachments/assets/06e062ad-211d-49a0-bda8-8cc982d7d096" />


-- Count products
![View All Products](<img width="1123" height="546" alt="image" src="https://github.com/user-attachments/assets/a5e223db-2a9c-4d79-b8e8-dca0982bc6eb" />)

```


## Author

**Name:** Mutsinzi Brian Heritier  
**ID:** 26522


