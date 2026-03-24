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
* **URL** `/login`
* **Method** POST
* **Header:**
    - Content-Type: application/json
* **Body:**
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
* **URL** `/logout`
* **Method** POST
* **Header:**
    - Content-Type: application/json

**Response**
- **Status Code:** 200 OK
```json
{
    "message": "Logout in succesfully."
}
```