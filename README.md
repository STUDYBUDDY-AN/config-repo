# StudyBuddy Configuration Repository

This repository hosts the centralized configuration for all StudyBuddy microservices, managed by the **Config Server**.

## Structure

The configuration files follow the standard Spring Cloud Config naming convention: `{application}-{profile}.yml`.

### Global Configuration
*   `application.yml`: Configuration shared across all services (e.g., global logging levels, common properties).

### Service-Specific Configuration
*   `gateway-server-{profile}.yml`: Configuration for the API Gateway.
*   `account-service-{profile}.yml`: Configuration for the Account Service.
*   `collaboration-service-{profile}.yml`: Configuration for the Collaboration Service.
*   `config-server-{profile}.yml`: Configuration for the Config Server itself.

## Profiles

*   `dev`: Development environment.
*   `qa`: Quality Assurance environment.
*   `prod`: Production environment.

## Usage

1.  **Config Server**: The Config Server connects to this repository to serve configurations to microservices.
2.  **Microservices**: Services specifically request their configuration on startup via the `spring.config.import` property (e.g., `optional:configserver:http://localhost:8888`).

## Secure Properties

Sensitive properties (passwords, secrets) should be encrypted using **Jasypt** or Spring Cloud Config's built-in encryption before being committed.
