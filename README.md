# Airbnb Clone Project

## Overview

The **Airbnb Clone Project** is a full-stack web application inspired by the core features and workflows of Airbnb. It is designed as a real-world simulation to help developers gain hands-on experience in building scalable, secure, and collaborative web platforms. This project is part of a larger learning objective focused on mastering backend development, API security, CI/CD integration, and effective team collaboration.

## Project Goals

- Build a fully functional booking platform clone with Django and MySQL.
- Model real-world data through relational database design.
- Develop and secure RESTful or GraphQL APIs.
- Collaborate effectively using GitHub and best practices in version control.
- Automate deployment using modern CI/CD tools like GitHub Actions and Docker.
- Learn to document and plan complex software systems.

## 👥 Team Roles

The success of this project depends on a collaborative team, each contributing distinct skills and responsibilities. Below are the key roles and their contributions to the Airbnb Clone Project:

### 🔧 Backend Developer
Responsible for designing and implementing the server-side logic, APIs, and core functionality using Django. Ensures business logic aligns with user workflows and integrates smoothly with the database and frontend.

### 🗄️ Database Administrator (DBA)
Designs and manages the relational database schema using MySQL. Handles data modeling, relationships, indexing, backup procedures, and ensures data integrity and performance.

### 🔐 Security Engineer
Implements security protocols to safeguard APIs and user data. Responsibilities include securing endpoints, handling authentication (e.g., token-based systems), authorization, and mitigating common vulnerabilities like SQL injection and XSS.

### 🚢 DevOps Engineer
Sets up and maintains the CI/CD pipeline using GitHub Actions and Docker. Responsible for automating deployment, monitoring build health, and ensuring that code changes flow seamlessly from development to production.

### 🧪 QA Engineer / Tester
Writes and executes test plans to ensure features function as intended. Performs unit, integration, and end-to-end testing. Validates performance, usability, and security aspects of the application.


## 🧰 Technology Stack

Below is an overview of the core technologies used in the Airbnb Clone Project, along with their specific roles in building a scalable and secure web application.

### 🐍 Django
A high-level Python web framework used to build the server-side logic of the application. Django enables rapid development of RESTful APIs, supports authentication, and follows the MVC (Model-View-Controller) architectural pattern.

### 🐬 MySQL
A relational database management system used to store and manage structured data for the platform, such as user accounts, property listings, bookings, and reviews. It supports ACID compliance, indexing, and complex relational queries.

### 🔗 GraphQL
A query language for APIs that allows clients to request only the data they need. It improves performance and flexibility over REST by enabling nested queries and real-time data fetching.

### 🐳 Docker
A containerization platform used to package the application and its dependencies into isolated environments. It ensures consistent development and deployment across different machines and cloud providers.

### 🔄 GitHub Actions
A CI/CD automation tool that runs tests, lints code, and deploys changes automatically whenever updates are pushed to the repository. It streamlines the development workflow and reduces human error during deployment.

### 🛠️ Git & GitHub
Version control and code collaboration tools used to manage changes to the project, coordinate team development, and maintain transparency throughout the software lifecycle.

### 📦 Postman
An API client tool used to test API endpoints, validate response data, and simulate client-server interactions during development and debugging.

### 🐚 Markdown
A lightweight markup language used for writing project documentation, including the `README.md`, setup guides, and API docs in a human-readable format.


## 🗃️ Database Design

This section outlines the core entities of the Airbnb Clone project and their relationships. The database is designed using a relational model (MySQL), optimized for scalability and data integrity.

### 👤 Users
Represents registered users of the platform (guests or hosts).

**Key Fields:**
- `id` (Primary Key)
- `name`
- `email`
- `password_hash`
- `user_type` (guest or host)

**Relationships:**
- A user can host multiple properties.
- A user can make multiple bookings.
- A user can write multiple reviews.

---

### 🏠 Properties
Represents the listings created by hosts for rent.

**Key Fields:**
- `id` (Primary Key)
- `title`
- `description`
- `location`
- `price_per_night`
- `host_id` (Foreign Key to Users)

**Relationships:**
- A property is owned by a user (host).
- A property can have multiple bookings.
- A property can have multiple reviews.

---

### 📅 Bookings
Captures booking transactions made by guests for a property.

**Key Fields:**
- `id` (Primary Key)
- `user_id` (Foreign Key to Users)
- `property_id` (Foreign Key to Properties)
- `start_date`
- `end_date`
- `status` (e.g., confirmed, cancelled)

**Relationships:**
- A booking is made by a user for a specific property.
- A booking can have one payment.

---

### 💳 Payments
Stores payment information related to bookings.

**Key Fields:**
- `id` (Primary Key)
- `booking_id` (Foreign Key to Bookings)
- `amount`
- `payment_method`
- `payment_status`

**Relationships:**
- A payment is associated with one booking.

---

### ✍️ Reviews
Represents user-generated feedback for properties.

**Key Fields:**
- `id` (Primary Key)
- `user_id` (Foreign Key to Users)
- `property_id` (Foreign Key to Properties)
- `rating` (1–5)
- `comment`

**Relationships:**
- A review is written by a user for a specific property.

---

### 🔗 Entity Relationships Summary

- One **User** can have many **Properties** (if the user is a host).
- One **User** can have many **Bookings** and **Reviews** (as a guest).
- One **Property** can have many **Bookings** and **Reviews**.
- One **Booking** has one **Payment**.
