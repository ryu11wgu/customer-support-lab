# Customer Support Lab

Application Support lab built with Java, Spring Boot, PostgreSQL, and REST APIs to practice incident troubleshooting, SQL validation, API debugging, and production-style support workflows.

## Purpose

This project simulates a small customer account system used for Application Support practice. The goal is to build realistic troubleshooting experience across common support layers:

- REST API requests
- Spring Boot backend logic
- PostgreSQL database access
- HTTP status codes
- validation errors
- database verification
- incident-style documentation

## Tech Stack

- Java 21
- Spring Boot
- Spring Web
- Spring Data JPA
- PostgreSQL
- Jakarta Validation
- Spring Boot Actuator
- Maven

## Current Features

- Create customer records
- Retrieve all customers
- Retrieve customer by ID
- Persist customer data in PostgreSQL
- Validate customer request data
- Expose basic Actuator health endpoint

## API Endpoints

| Method | Endpoint              | Description              |
| ------ | --------------------- | ------------------------ |
| GET    | `/api/customers`      | Get all customers        |
| GET    | `/api/customers/{id}` | Get customer by ID       |
| POST   | `/api/customers`      | Create a customer        |
| GET    | `/actuator/health`    | Check application health |

## Customer Fields

| Field     | Description                                   |
| --------- | --------------------------------------------- |
| id        | Auto-generated customer ID                    |
| firstName | Customer first name                           |
| lastName  | Customer last name                            |
| email     | Unique customer email                         |
| status    | Customer status: ACTIVE, SUSPENDED, or CLOSED |
| createdAt | Timestamp created                             |
| updatedAt | Timestamp last updated                        |

## Example Create Customer Request

```
curl -X POST http://localhost:8081/api/customers \
  -H "Content-Type: application/json" \
  -d '{
    "firstName": "John",
    "lastName": "Smith",
    "email": "john.smith@example.com",
    "status": "ACTIVE"
  }'
```

## Example Database Verification

```
SELECT * FROM customers;
```

## Configuration

This project expects database credentials to be provided through environment variables.

```
spring:
  datasource:
    url: jdbc:postgresql://localhost:5432/customer_support_lab
    username: ${DB_USERNAME}
    password: ${DB_PASSWORD}
```

Example local environment setup:

```
export DB_USERNAME=your_postgres_user
export DB_PASSWORD='your_postgres_password'
```

## Running the Application

```
./mvnw spring-boot:run
```

Then test:

```
curl http://localhost:8081/actuator/health
```

Expected response:

```
{
  "status": "UP"
}
```

## Support Skills Practiced

- Testing REST APIs with curl
- Reading Spring Boot startup logs
- Troubleshooting PostgreSQL connection errors
- Validating database records with SQL
- Identifying request validation failures
- Understanding layered backend architecture
- Mapping issues across controller, service, repository, and database layers

## Completed Milestones

- Set up Spring Boot project
- Connected Spring Boot to PostgreSQL
- Created Customer entity and CustomerStatus enum
- Created CustomerRepository
- Created CustomerService layer
- Created CustomerController
- Added validation for customer fields
- Tested POST and GET requests with curl
- Verified persisted records directly in PostgreSQL

## Planned Support Labs

- App fails to start due to bad database credentials
- API returns 400 for invalid customer request
- API returns 404 for missing customer
- API returns 500 for simulated backend error
- Customer status mismatch investigation
- Slow endpoint troubleshooting
- Actuator and basic observability checks
