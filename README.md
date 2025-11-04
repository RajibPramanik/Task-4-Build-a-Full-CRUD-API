# Task-4-Build-a-Full-CRUD-API

# Spring Boot CRUD API - Product Management

A simple RESTful API built with **Spring Boot** to manage products in a MySQL database. This API allows for **Create**, **Read**, **Update**, and **Delete** (CRUD) operations on product data. It also includes input validation, error handling, and responses in **JSON format**.

## Features

- Full **CRUD operations** for products
- **Product search** by name
- **Filtering products** by category and price
- **Global exception handling** for better error reporting
- **Input validation** for product name and price
- **MySQL database** integration for data persistence

## Technologies

- **Java 21**
- **Spring Boot 3.4.5**
- **Spring Data JPA**
- **MySQL**
- **Maven** for project management
- **Jakarta Validation** for input validation

## Prerequisites

Before you can run the project, make sure you have the following installed:

- **JDK 21** or later
- **Maven 3.9+**
- **MySQL Server** running locally or remotely

## Database Configuration

The application connects to a MySQL database. You need to configure your database connection settings in the `application.properties` file.

Update the following properties with your MySQL credentials:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/your_db_name
spring.datasource.username=your_username
spring.datasource.password=your_password
spring.jpa.hibernate.ddl-auto=update
````

## Setup & Running the Application

1. **Clone the repository:**

   ```bash
   git clone https://github.com/yourusername/spring-boot-crud-api.git
   ```

2. **Navigate to the project directory:**

   ```bash
   cd spring-boot-crud-api
   ```

3. **Build the project using Maven:**

   ```bash
   ./mvnw clean install
   ```

4. **Run the application:**

   ```bash
   ./mvnw spring-boot:run
   ```

The application will start and be available at [http://localhost:8080](http://localhost:8080).

## API Endpoints

### **1. Get all products**

* **Endpoint:** `GET /api/products`
* **Description:** Retrieves a list of all products in the database.
* **Response Example:**

  ```json
  [
    {
      "id": 1,
      "name": "Product Name",
      "description": "Product Description",
      "price": 99.99,
      "category": "Category Name"
    },
    ...
  ]
  ```

### **2. Get a specific product by ID**

* **Endpoint:** `GET /api/products/{id}`
* **Description:** Retrieves a product by its ID.
* **Response Example:**

  ```json
  {
    "id": 1,
    "name": "Product Name",
    "description": "Product Description",
    "price": 99.99,
    "category": "Category Name"
  }
  ```

### **3. Get products by category**

* **Endpoint:** `GET /api/products/category/{categoryName}`
* **Description:** Retrieves a list of products filtered by category.
* **Response Example:**

  ```json
  [
    {
      "id": 2,
      "name": "Product 2",
      "description": "Product Description",
      "price": 79.99,
      "category": "Electronics"
    },
    ...
  ]
  ```

### **4. Get products with price less than or equal to max price**

* **Endpoint:** `GET /api/products/price/{maxPrice}`
* **Description:** Retrieves products filtered by price.
* **Response Example:**

  ```json
  [
    {
      "id": 1,
      "name": "Product 1",
      "description": "Product Description",
      "price": 49.99,
      "category": "Category Name"
    },
    ...
  ]
  ```

### **5. Search products by name**

* **Endpoint:** `GET /api/products/search?name={name}`
* **Description:** Retrieves a list of products that match the search query for product name.
* **Response Example:**

  ```json
  [
    {
      "id": 1,
      "name": "Product Name",
      "description": "Product Description",
      "price": 99.99,
      "category": "Category Name"
    },
    ...
  ]
  ```

### **6. Create a new product**

* **Endpoint:** `POST /api/products`

* **Description:** Adds a new product to the database.

* **Request Example:**

  ```json
  {
    "name": "New Product",
    "description": "Product Description",
    "price": 49.99,
    "category": "Category Name"
  }
  ```

* **Response Example:**

  ```json
  {
    "id": 1,
    "name": "New Product",
    "description": "Product Description",
    "price": 49.99,
    "category": "Category Name"
  }
  ```

### **7. Update an existing product**

* **Endpoint:** `PUT /api/products/{id}`

* **Description:** Updates an existing product by ID.

* **Request Example:**

  ```json
  {
    "name": "Updated Product",
    "description": "Updated Description",
    "price": 59.99,
    "category": "Updated Category"
  }
  ```

* **Response Example:**

  ```json
  {
    "id": 1,
    "name": "Updated Product",
    "description": "Updated Description",
    "price": 59.99,
    "category": "Updated Category"
  }
  ```

### **8. Delete a product**

* **Endpoint:** `DELETE /api/products/{id}`
* **Description:** Deletes a product by ID.
* **Response Example:**

  ```json
  {
    "message": "Product with ID 1 has been deleted successfully."
  }
  ```

## Error Handling

The API includes global exception handling to provide meaningful error messages in case of:

* **Resource not found** (e.g., when a product is not found by ID).
* **Validation errors** (e.g., invalid product data).
* **Server errors** (e.g., database connection issues).

Example of an error response:

```json
{
  "status": "error",
  "message": "Product not found with ID 1"
}
```

## Data Validation

The API validates product input to ensure:

* Product name **cannot be blank**.
* Product price must be a **positive value**.

Example of validation error:

```json
{
  "status": "error",
  "message": "Product name cannot be blank."
}
```

## Folder Structure

The project follows the standard Spring Boot structure:

```
src/main/java/com/spring_boot_rest_api/
    ├── controller/      # REST controllers for handling HTTP requests
    ├── model/          # Data models representing products
    ├── repository/     # Repository layer for interacting with the database
    ├── service/        # Service layer for business logic
    └── exception/      # Exception handling and custom error responses
```

### **Explanation of the README**:

- **Introduction:** Brief overview of the project and its purpose.
- **Features:** List of key features implemented.
- **Technologies:** Tools and libraries used in the project.
- **Prerequisites:** Requirements to run the project.
- **Database Configuration:** Details on how to configure MySQL connection.
- **Setup & Running:** Step-by-step instructions for cloning, building, and running the application.
- **API Endpoints:** Detailed description of each API endpoint with request/response examples.
- **Error Handling:** Explanation of the global error handling and common error messages.
- **Data Validation:** Description of input validation rules.
- **Folder Structure:** Overview of the project structure for better understanding.

---
This README provides a thorough and clear explanation of your project. It also includes good practices like showing example requests and responses for each API endpoint, explaining how to run the project, and providing error-handling information.
