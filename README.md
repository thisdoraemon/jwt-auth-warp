# Rust Auth Server Using Warp API

This documentation provides an overview and usage guide for the Rust Auth Server implemented using the Warp API. The server includes authentication with JWT (JSON Web Token) and supports different user roles.

## Table of Contents
- Introduction
- Dependencies
- Project Structure
- Authentication
- Routes
    - Login Route
    - User Route
    - Admin Route
- Error Handling

## 1. Introduction

The Rust Auth Server is a simple authentication server built using the Warp API. It supports user login, user-specific routes, and admin-specific routes. The authentication is based on JSON Web Tokens (JWT) and includes user roles (User, Admin).

## 2. Dependencies

 warp: A web framework for Rust.
 
 serde: A serialization and deserialization library.
 
 jsonwebtoken: A library for encoding and decoding JWT.
 
 chrono: A date and time handling library.
 
 thiserror: A library for defining custom errors.
 
## 3. Project Structure

The project is structured into multiple modules:

auth: Contains authentication-related functions and structures.

error: Defines custom error types and a rejection handler.

main.rs: The main entry point for the application.

## 4. Authentication

The authentication process is based on JWT. The server generates a JWT token upon successful login, and this token is required for accessing protected routes. The token contains information about the user's ID, role, and expiration time.

## 5. Routes
  ### 5.1 Login Route 
  
    Path: /login
    Method: POST
    Payload: JSON object with email and pw fields.
    Response: JSON object with a token field upon successful login.

### 5.2 User Route

    Path: /user
    Method: GET
    Authorization: Requires a valid JWT token with a User role.
    Response: A greeting message for the authenticated user.

### 5.3 Admin Route 

    Path: /admin
    Method: GET
    Authorization: Requires a valid JWT token with an Admin role.
    Response: A greeting message for the authenticated admin.

## 6. Error Handling 

The server uses a custom error module (error.rs) to handle various error scenarios. Errors include wrong credentials, JWT token issues, missing authentication headers, and permission errors. The rejection handler converts these errors into appropriate HTTP responses with corresponding status codes and error messages.

*Note: This documentation assumes basic familiarity with Rust, Warp, and JWT concepts. For more details on specific functions and implementations, refer to the source code.*
