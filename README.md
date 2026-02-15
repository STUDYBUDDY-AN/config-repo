# StudyBuddy Configuration Repository

This repository hosts the centralized configuration for all StudyBuddy microservices.

## Structure

The configuration files follow the standard Spring Cloud Config naming convention: `{application}-{profile}.yml`.

*   **Global Configuration:**
    *   `application.yml`: Configuration shared across all services.

*   **Service-Specific Configuration:**
    *   `gateway-server-{profile}.yml`
    *   `account-service-{profile}.yml`
    *   `collaboration-service-{profile}.yml`
    *   `config-server-{profile}.yml`

## Profiles

*   `dev`: Development environment.
*   `qa`: Quality Assurance environment.
*   `prod`: Production environment.

## Secure Properties

Sensitive properties (passwords, secrets) should be encrypted using Jasypt or Spring Cloud Config's built-in encryption before being committed.
