# Spring Boot JWT Security Demo

This project demonstrates the implementation of security using **Spring Boot 3.4.4** and **JSON Web Tokens (JWT)**. It showcases user authentication, role-based authorization, and secure API access with Spring Security.

---

## 🔐 Features

- ✅ User registration and login with JWT authentication  
- 🔒 Password encryption using BCrypt  
- 👤 Role-based authorization with Spring Security  
- ❌ Customized access denied handling  
- 🔓 Logout mechanism  
- ♻️ Refresh token functionality  

---

## 🛠️ Technologies Used

- **Spring Boot 3.4.4**
- **Spring Security**
- **JSON Web Tokens (JWT)**
- **BCrypt**
- **Maven**

---

## 🚀 Getting Started

### Prerequisites

- Java 17+
- Maven
- Git

### Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/yassinemh3/jwt-auth-spring-boot.git
   cd spring-boot-jwt-security-demo
   ```
2. **Docker compose**
    ```bash
    docker-compose up
   ```
3. **Build the project**
  ```bash
  mvn clean install
  ```
4. **Run the application**
  ```bash
  mvn spring-boot:run
  ```
## Roles & Permissions

### Roles

| Role    | Permissions                                                                                 |
|---------|----------------------------------------------------------------------------------------------|
| USER    | No specific permissions (default role with basic access)                                     |
| MANAGER | - MANAGER_READ<br>- MANAGER_CREATE<br>- MANAGER_UPDATE<br>- MANAGER_DELETE                   |
| ADMIN   | All MANAGER permissions plus:<br>- ADMIN_READ<br>- ADMIN_CREATE<br>- ADMIN_UPDATE<br>- ADMIN_DELETE |

---
## 🔧 API Endpoints Overview

| Method | Endpoint                   | Description                  | Secured |
|--------|----------------------------|------------------------------|---------|
| POST   | `/api/v1/auth/register`    | Register new user            | No      |
| POST   | `/api/v1/auth/authenticate`| Login & get JWT              | No      |
| POST   | `/api/v1/auth/refresh`     | Refresh token                | No      |
| PATCH  | `/api/v1/users`            | Change password              | Yes     |
| GET    | `/api/v1/demo-controller`  | Demo secured endpoint        | Yes     |
| POST   | `/api/v1/books`            | Create or update a book      | Yes     |
| GET    | `/api/v1/books`            | Get all books                | Yes     |

##API Usage Examples
1. **Register User**
```bash
POST http://localhost:8080/api/v1/auth/register
Content-Type: application/json

{
  "firstname": "user",
  "lastname": "1",
  "email": "user1@mail.com",
  "password": "password",
  "role": "ADMIN"
}
```
2. **Login Again and Update Token**
```bash
POST http://localhost:8080/api/v1/auth/authenticate
Content-Type: application/json

{
  "email": "user@mail.com",
  "password": "newPassword"
}
```
3. **Change the Password**
```bash
PATCH http://localhost:8080/api/v1/users
Content-Type: application/json
Authorization: Bearer {{auth-token}}

{
  "currentPassword": "password",
  "newPassword": "newPassword",
  "confirmationPassword": "newPassword"
}
```
4. **Create a New Book**
```bash
POST http://localhost:8080/api/v1/books
Authorization: Bearer {{auth-token}}
Content-Type: application/json

{
  "author": "user1",
  "isbn": "12345"
}
```
