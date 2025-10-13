# E-Commerce Microservices

This is a comprehensive e-commerce platform built with a microservices architecture. It demonstrates a robust, scalable, and observable system using modern technologies.

## Overview

The platform is composed of several microservices that work together to provide a full-featured e-commerce experience. It includes services for product management, inventory control, order processing, and payments. The system is designed to be resilient and observable, with a full observability stack included.

## Modules

The project is divided into the following modules:

*   **API Gateway:** The single entry point for all client requests. It routes requests to the appropriate microservices and handles cross-cutting concerns like security and rate limiting.
*   **Discovery Service:** Allows microservices to find and communicate with each other without hardcoding hostnames and ports.
*   **Product Service:** Manages the product catalog.
*   **Inventory Service:** Manages the stock levels of products.
*   **Order Service:** Handles the creation and management of customer orders.
*   **Payment Service:** Processes payments for orders.
*   **Observability:** Contains the configuration for the observability stack, including Prometheus, Grafana, and Loki.

## Getting Started

To get the platform running, you'll need to have Docker and Docker Compose installed.

1.  **Clone the repository:**

    ```bash
    git clone https://github.com/dejesusbg/ecommerce.git
    cd ecommerce
    ```

2.  **Build and run the services:**

    ```bash
    docker-compose up --build
    ```

    This will build the Docker images for each microservice and start all the services defined in the `docker-compose.yml` file.

3.  **Access the services:**

    Once all the services are running, you can access them at the following URLs:

    *   **API Gateway:** http://localhost:8080
    *   **Discovery Service (Eureka):** http://localhost:8761
    *   **Keycloak:** http://localhost:8180
    *   **Prometheus:** http://localhost:9090
    *   **Grafana:** http://localhost:3000
    *   **Loki:** http://localhost:3100

## Services

This section provides a brief overview of each microservice and its responsibilities.

### API Gateway

*   **Description:** The single entry point for all client requests. It is responsible for routing requests to the appropriate microservices, as well as handling cross-cutting concerns such as security, monitoring, and resilience.
*   **Technologies:** Spring Cloud Gateway, Resilience4j, Spring Security.

### Discovery Service

*   **Description:** A service registry that allows microservices to dynamically discover and communicate with each other.
*   **Technologies:** Spring Cloud Netflix Eureka.

### Product Service

*   **Description:** Manages the product catalog, including creating, retrieving, updating, and deleting products.
*   **Technologies:** Spring Boot, Spring Data MongoDB, Redis for caching.

### Inventory Service

*   **Description:** Manages the inventory levels for each product.
*   **Technologies:** Spring Boot, Spring Data JPA, PostgreSQL.

### Order Service

*   **Description:** Handles all aspects of order management, including creating orders, retrieving order details, and updating order statuses. It communicates with the Product, Inventory, and Payment services.
*   **Technologies:** Spring Boot, Spring Data JPA, PostgreSQL, Feign Client.

### Payment Service

*   **Description:** Processes payments for orders.
*   **Technologies:** Spring Boot, Spring Data JPA, PostgreSQL.

## API Endpoints

The API Gateway exposes the following endpoints. All endpoints are prefixed with `/api`.

| Method | Path                  | Service             | Description                  |
| ------ | --------------------- | ------------------- | ---------------------------- |
| GET    | `/products`           | Product Service     | Get all products             |
| GET    | `/products/{id}`      | Product Service     | Get a product by ID          |
| POST   | `/products`           | Product Service     | Create a new product         |
| PUT    | `/products/{id}`      | Product Service     | Update a product             |
| DELETE | `/products/{id}`      | Product Service     | Delete a product             |
| GET    | `/inventory/{sku}`    | Inventory Service   | Get inventory for a SKU      |
| POST   | `/orders`             | Order Service       | Create a new order           |
| GET    | `/orders/{id}`        | Order Service       | Get an order by ID           |
| POST   | `/payments`           | Payment Service     | Process a payment            |

## Observability

The platform includes a comprehensive observability stack to monitor the health and performance of the microservices.

*   **Prometheus:** A monitoring and alerting toolkit that collects metrics from the microservices. You can access the Prometheus dashboard at http://localhost:9090.
*   **Grafana:** A visualization tool that allows you to create dashboards to monitor the metrics collected by Prometheus. You can access Grafana at http://localhost:3000.
*   **Loki:** A log aggregation system that collects logs from all the microservices. You can use Grafana to query and visualize the logs.
