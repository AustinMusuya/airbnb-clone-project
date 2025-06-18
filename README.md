# Airbnb Clone Project

## Overview

The **Airbnb Clone Project** is a full-stack web application that replicates the core functionalities of Airbnb’s booking platform. This project emphasizes real-world development practices, focusing on scalable architecture, secure API design, and collaborative workflows. It simulates a production-grade environment to give learners hands-on experience with modern software development techniques, backend infrastructure, and deployment pipelines.

## Project Goals

- Design and build a robust backend architecture using Django and PostgreSQL.
- Practice feature-driven development by implementing core functionalities like user authentication, property listing, booking, and reviews.
- Apply advanced API security measures to protect user data and ensure safe transactions.
- Structure and document a relational database schema that supports the platform’s logic.
- Integrate CI/CD tools for efficient, automated testing and deployment.
- Collaborate using GitHub following industry-standard branching and pull request workflows.
- Gain exposure to GraphQL integration for modern API design.

## Technology Stack

- **Django**: A high-level Python web framework used to build RESTful APIs and manage server-side logic.
- **PostgreSQL**: A reliable relational database system used to store user, property, booking, and transaction data.
- **GraphQL**: A query language for APIs that allows clients to request specific data, improving performance and flexibility.
- **JWT (JSON Web Tokens)**: Used for user authentication and secure session management.
- **Docker**: Containerization tool to package and run the application consistently across different environments.
- **GitHub Actions**: CI/CD tool used to automate testing and deployment workflows.
- **Git & GitHub**: Version control and collaboration platform for managing codebase and team contributions.
- **Markdown**: Used for writing clear and structured project documentation, including this README.

## Team Roles

- **Backend Developer**: Responsible for designing and implementing API endpoints, business logic, and integrating the database.
- **Database Administrator (DBA)**: Designs and manages the database schema, ensures data integrity, and optimizes queries.
- **DevOps Engineer**: Handles CI/CD pipelines, containerization, deployment, and monitoring systems.
- **Security Engineer**: Implements authentication, authorization, and other protective measures to secure APIs and sensitive data.
- **Project Manager**: Coordinates task allocation, manages timelines, and ensures successful project delivery.
- **Technical Writer**: Prepares project documentation including API docs, database schema descriptions, and team workflows.

## Database Design

### Entities & Key Fields

- **User**
  - id (Primary Key)
  - username
  - email
  - password_hash
  - is_host (Boolean)

- **Property**
  - id (Primary Key)
  - host_id (Foreign Key to User)
  - title
  - description
  - price_per_night

- **Booking**
  - id (Primary Key)
  - user_id (Foreign Key to User)
  - property_id (Foreign Key to Property)
  - start_date
  - end_date

- **Review**
  - id (Primary Key)
  - user_id (Foreign Key to User)
  - property_id (Foreign Key to Property)
  - rating
  - comment

- **Payment**
  - id (Primary Key)
  - booking_id (Foreign Key to Booking)
  - amount
  - payment_status
  - payment_date

### Relationships

- A **User** can own multiple **Properties**.
- A **User** can make multiple **Bookings**, each linked to one **Property**.
- A **Review** is written by a **User** for a **Property**.
- A **Payment** is tied to a **Booking**.

## Feature Breakdown

- **User Management**  
  Allows users to register, log in, and manage their profiles. Supports role distinction between guests and hosts.

- **Property Management**  
  Enables hosts to list new properties, update details, and remove listings. Properties include attributes like location, price, and amenities.

- **Booking System**  
  Users can book available properties by selecting dates and submitting reservations. The system checks availability and prevents date conflicts.

- **Reviews and Ratings**  
  After a completed booking, users can rate and leave feedback on a property, helping maintain quality and trust in the platform.

- **Payment Integration**  
  Captures and records payments associated with bookings. Ensures each transaction is linked to a user and a property booking.

- **Search and Filtering**  
  Users can search for properties using filters like location, date range, price, and rating to find relevant options.

## API Security

- **Authentication (JWT)**: Users must log in to receive a token used to authenticate subsequent requests. This ensures only verified users can access protected routes.
- **Authorization**: Permissions ensure users can only access or modify their own data (e.g., only a host can edit their listings).
- **Rate Limiting**: Prevents abuse of the API by limiting the number of requests from a single IP or token in a given time window.
- **Input Validation & Sanitization**: Protects against injection attacks and ensures incoming data is clean and safe.
- **HTTPS Enforcement**: All traffic should be encrypted in production to prevent man-in-the-middle attacks.

### Why Security Matters

- **User Data Protection**: Secures personal details like email, address, and payment information.
- **Business Integrity**: Prevents unauthorized bookings, fake listings, and financial fraud.
- **System Reliability**: Ensures consistent availability and reduces exposure to automated abuse and denial-of-service attacks.

## CI/CD Pipeline

- **CI/CD (Continuous Integration & Continuous Deployment)** ensures that code changes are automatically tested and deployed with minimal manual effort.

### Why It Matters

- Reduces deployment errors and manual testing effort.
- Encourages smaller, faster, and more reliable updates.
- Enhances developer confidence through automated testing and rollback options.

### Tools Used

- **GitHub Actions**: Automates linting, testing, and deployment pipelines on every push and pull request.
- **Docker**: Ensures consistent development and deployment environments across all team members and hosting platforms.
