# E-commerce API
E-commerce API is a RESTful backend built with Flask that handles user authentication, product management, and shopping cart operations. It provides session-based authentication using Flask-Login and allows users to manage products and simulate a simple e-commerce flow (add to cart and checkout).
<div align="center">

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Flask](https://img.shields.io/badge/flask-%23000.svg?style=for-the-badge&logo=flask&logoColor=white)
![SQLAlchemy](https://img.shields.io/badge/sqlalchemy-%23D71F00.svg?style=for-the-badge&logo=sqlalchemy&logoColor=white)
![SQLite](https://img.shields.io/badge/sqlite-%2307405e.svg?style=for-the-badge&logo=sqlite&logoColor=white)
</div>

# Technologies
- Python
- Flask
- Flask-SQLAlchemy
- Flask-Login
- Flask-CORS
- SQLite

# Authentication Endpoints
This API uses session-based authentication with Flask-Login. After login, a session cookie is created and automatically sent in requests, which can be obtained from the following route.

## 1. Login `/login`
Generates a cookie for authentication.

**Request**
- **URL:** `/login`
- **Method:** POST
- **Header:**
    - Content-Type: application/json
- **Body:**
```json
{
    "username": "admin", // example
    "password": "password123"
}
```

**Response**
- **Status Code:** 200 OK
- **Body:**
```json
{
    "message": "Logged in succesfully."
}
```

## 2. Logout `/logout`
Ends the user session **(Requires Authentication)**

**Request**
- **URL:** `/logout`
- **Method:** POST
- **Header:**
    - Content-Type: application/json

**Response**
- **Status Code:** 200 OK
```json
{
    "message": "Logout in succesfully."
}
```

# Endpoints
Below are all the endpoints. Some require authentication.

## Product Endpoints
## 1. POST `/api/products/add`
Add a new product. **(Require Authentication)**

**Request**
- **URL:** `/api/products/add`
- **Method:** POST
- **Header:**
    - Content-Type: application/json
- **Body:**
```json
{
    "name": "TV",
    "price": 3999,
    "description": "Smart TV 4K"
}
```

**Response**
- **Status Code:** 200 OK
- **Body:**
```json
{
    "message": "Product added succesfully."
}
```

## 2. GET `/api/products`
Returns all registered products. **(Require Authentication)**

**Request**
- **URL:** `/api/products`
- **Method:** GET

**Response**
- **Status Code:** 200 OK
- **Body:**
```json
{
    [
    {
        "id": 1,
        "name": "TV",
        "price": 4000.0
    },
    {
        "id": 2,
        "name": "Notebook",
        "price": 2500.0
    }
]
}
```

## 3. GET `/api/products/{product_id}`
Returns the data for a specific product. **(Require Authentication)**

**Request**
- **URL:** `/api/products//{product_id}`
- **Method:** GET

**Response**
- **Status Code:** 200 OK
- **Body: (using product_id = 1)**
```json
{
    {
        "id": 1,
        "name": "TV",
        "price": 4000.0
    }
}
```

## Possible Errors
**Error - Product not Found**
- **Status Code:** 404 Not Found
- **Body:**
```json
{
    "message": "Product not found."
}
```

## 4. DELETE `/api/products/delete/{product_id}`
Delete a product. **(Require Authentication)**

**Request**
- **URL:** `/api/products/delete/{product_id}`
- **Method:** DELETE

**Response**
- **Status Code:** 200 OK
- **Body: (using product_id = 2)**
```json
{
    "message": "Product deleted succesfully."
}
```

## Possible Errors
**Error - Product not Found to delete**
- **Status Code:** 404 Not Found
- **Body:**
```json
{
    "message": "Product not found to delete."
}
```

## 5. PUT `/api/products/update/{product_id}`
Update a product. **(Require Authentication)**

**Request**
- **URL:** `/api/products/update/{product_id}`
- **Method:** PUT
- **Header:**
    - Content-Type: application/json
- **Body: (using product_id = 1)**
```json
{
    "price": 4000 // Update only the price.
}
```

**Response**
- **Status Code:** 200 OK
- **Body:**
```json
{
    "message": "Product updated succesfully."
}
```

## Possible Errors
**Error - Product not Found to update**
- **Status Code:** 404 Not Found
- **Body:**
```json
{
    "message": "Product not found to update."
}
```

## Cart
## 1. POST `/api/cart/add/{product_id}`
Add a product to the user's cart. **(Require Authentication)**

**Request**
- **URL:** `/api/cart/add/{product_id}`
- **Method:** POST
- **Header:**
    - Content-Type: application/json

**Response**
- **Status Code:** 200 OK
- **Body: (Using product_id = 1)**
```json
{
    "message": "Item added to the cart succesfully."
}
```

## Possible Errors
**Error - Failed to add product.**
- **Status Code:** 400 Bad Request
- **Body:**
```json
{
    "message": "Failed to add item to the cart."
}
```

## 2. GET `/api/cart`
Returns the products in the user's cart based on their login. **(Require Authentication)**

**Request**
- **URL:** `/api/cart`
- **Method:** GET

**Response**
- **Status Code:** 200 OK
- **Body:**
```json
[
    {
        "id": 1,
        "product_id": 1,
        "user_id": 1
    }
]
```

## 3. DELETE `/api/cart/remove/{product_id}`
Remove a product from user's cart. **(Require Authentication)**

**Request**
- **URL:** `/api/cart/remove/{product_id}`
- **Method:** DELETE

**Response**
- **Status Code:** 200 OK
- **Body: (using product_id = 1)**
```json
{
    "message": "Item removed from the cart succesfully."
}
```

## 4. POST `/api/cart/checkout`
Complete the cart checkout process. **(Require Authentication)**

**Request**
- **URL:** `/api/cart/checkout`
- **Method:** POST
- **Header:**
    - Content-Type: application/json

**Response**
- **Status Code:** 200 OK
- **Body:**
```json
{
    "message": "Checkout succesfully."
}
```

# Requirements
Dependencies used in this project:

```text
Flask==2.3.0
Flask-SQLAlchemy==3.1.1
Flask-Login==0.6.2
Flask-Cors==3.0.10
Werkzeug==2.3.0
```
To install all dependencies, run the following command **(Make sure Python and pip are installed on your system.)**:
```bash
pip install -r requirements.txt
```

# Next Features
- Separate responsibilities (Model, Services, Routes)
- Connect to the database externally.
- Improve error handling.

> If you have any questions or suggestions, feel free to open an issue or get in touch.