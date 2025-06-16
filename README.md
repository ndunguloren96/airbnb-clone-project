# Overview of the AirBnB Clone

## Objective
The backend for the Airbnb Clone project is designed to provide a robust and scalable foundation for managing user interactions, property listings, bookings, and payments. This backend supports core Airbnb features, ensuring a seamless experience for both users and hosts.

## Project Goals
- **User Management**: Secure system for user registration, authentication, and profile handling.
- **Property Management**: Endpoints to create, update, and manage property listings.
- **Booking System**: Reserve properties with full lifecycle management.
- **Payment Processing**: Integrated and secure transaction system.
- **Review System**: Users can leave ratings and feedback on properties.
- **Data Optimization**: Indexing and caching for high-performance queries.

##  Feature Breakdown

### 1. API Documentation
- **OpenAPI Standard**: API endpoints documented clearly for easy integration.
- **Django REST Framework**: Handles CRUD operations on user and property data.
- **GraphQL**: Enables flexible and efficient queries.

### 2. User Authentication
- **Endpoints**: `/users/`, `/users/{user_id}/`
- **Features**: User registration, login, profile management.

### 3. Property Management
- **Endpoints**: `/properties/`, `/properties/{property_id}/`
- **Features**: Add, edit, delete, and view property listings.

### 4. Booking System
- **Endpoints**: `/bookings/`, `/bookings/{booking_id}/`
- **Features**: Full booking lifecycle: create, update, check-in, check-out.

### 5. Payment Processing
- **Endpoints**: `/payments/`
- **Features**: Securely handle payments linked to bookings.

### 6. Review System
- **Endpoints**: `/reviews/`, `/reviews/{review_id}/`
- **Features**: Create and manage reviews per property.

### 7. Database Optimizations
- **Indexing**: Accelerates queries on frequent access fields.
- **Caching**: Reduces load on DB, increases response speed.

---

## Technology Stack
- **Django** – Python web framework.
- **Django REST Framework** – RESTful APIs.
- **PostgreSQL** – Relational database.
- **GraphQL** – Query language for APIs.
- **Celery** – Asynchronous task queue.
- **Redis** – Cache and session management.
- **Docker** – Containerization for consistency.
- **GitHub Actions** – CI/CD automation.

---

## Team Roles
- **Backend Developer**: API endpoints, logic, database schemas.
- **Database Administrator**: Schema design, performance tuning.
- **DevOps Engineer**: CI/CD, deployment, system monitoring.
- **QA Engineer**: Testing and quality control.

---

## API Documentation Overview
- **REST API**: Full documentation via OpenAPI.
- **GraphQL API**: Flexible queries for frontend integration.

---

## Endpoints Overview

### Users
- `GET /users/` - List all users  
- `POST /users/` - Create a new user  
- `GET /users/{user_id}/` - Retrieve specific user  
- `PUT /users/{user_id}/` - Update specific user  
- `DELETE /users/{user_id}/` - Delete specific user  

### Properties
- `GET /properties/` - List all properties  
- `POST /properties/` - Create new property  
- `GET /properties/{property_id}/` - Get specific property  
- `PUT /properties/{property_id}/` - Update specific property  
- `DELETE /properties/{property_id}/` - Delete specific property  

### Bookings
- `GET /bookings/` - List all bookings  
- `POST /bookings/` - Create booking  
- `GET /bookings/{booking_id}/` - Retrieve booking  
- `PUT /bookings/{booking_id}/` - Update booking  
- `DELETE /bookings/{booking_id}/` - Cancel booking  

### Payments
- `POST /payments/` - Process payment  

### Reviews
- `GET /reviews/` - List all reviews  
- `POST /reviews/` - Create review  
- `GET /reviews/{review_id}/` - Retrieve review  
- `PUT /reviews/{review_id}/` - Update review  
- `DELETE /reviews/{review_id}/` - Delete review  

---

##  Database Design

### Entities and Key Fields

#### Users
- `id` (Primary Key)  
- `email`  
- `password`  
- `full_name`  
- `is_host`  

#### Properties
- `id` (Primary Key)  
- `title`  
- `location`  
- `price_per_night`  
- `owner_id` (FK → Users)  

#### Bookings
- `id` (Primary Key)  
- `property_id` (FK → Properties)  
- `user_id` (FK → Users)  
- `check_in_date`  
- `check_out_date`  

#### Reviews
- `id` (Primary Key)  
- `property_id` (FK → Properties)  
- `user_id` (FK → Users)  
- `rating`  
- `comment`  

#### Payments
- `id` (Primary Key)  
- `booking_id` (FK → Bookings)  
- `amount`  
- `status`  
- `payment_method`  

### Relationships
- A **User** can list multiple **Properties**.  
- A **Booking** is made by a **User** for a specific **Property**.  
- A **Payment** is linked to a single **Booking**.  
- A **Review** is created by a **User** for a **Property**.

---

##  API Security

### Key Security Measures
- **Authentication**: JWT-based token authentication to ensure only verified users access protected endpoints.
- **Authorization**: Role-based permissions to restrict access (e.g., only hosts can list properties).
- **Rate Limiting**: Protects against abuse (e.g., brute-force login attempts).
- **Input Validation**: Prevents injection attacks and invalid data submission.
- **HTTPS Only**: Enforces secure communication via SSL.

### Why Security Matters
- **User Data Protection**: Ensures sensitive user details are not leaked or compromised.
- **Payment Integrity**: Maintains the confidentiality and integrity of financial transactions.
- **Service Reliability**: Prevents abuse and denial-of-service via rate limits and monitoring.
- **Compliance**: Helps align with data protection laws (e.g., GDPR).

---

##  CI/CD Pipeline

### What is CI/CD?
**CI/CD** stands for **Continuous Integration** and **Continuous Deployment/Delivery**. It automates the integration of code changes, testing, and deployment, ensuring faster and safer releases.

### Importance in This Project
- **Consistency**: Automatically builds, tests, and deploys code to maintain high quality.
- **Speed**: Shortens the time between development and deployment.
- **Reliability**: Prevents bugs from reaching production through automated tests and checks.
- **Scalability**: Easily deploys to different environments (development, staging, production).

### Tools Used
- **GitHub Actions**: Automates test and deployment workflows on each push or pull request.
- **Docker**: Creates reproducible development and deployment environments.
- **Heroku/DigitalOcean/Render** *(example deployment targets)*: Hosts the deployed application with integration to CI/CD pipeline.

---
