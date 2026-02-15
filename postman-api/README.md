# StudyBuddy Postman Collection

This directory contains the Postman Collection and Environment files for testing the StudyBuddy microservices via the API Gateway.

## Files

*   **`StudyBuddy_Collection.json`**: The API collection containing updated endpoints for Account Service and Collaboration Service.
*   **`StudyBuddy_Environment.json`**: The environment file containing variables for `dev` (localhost).

## Setup

1.  **Import** both files into Postman.
2.  **Select Environment**: Choose **"StudyBuddy - Local (Dev)"** from the environment dropdown in Postman.
3.  **Variables**:
    *   `baseUrl`: Defaults to `http://localhost:8080` (Gateway).
    *   `userId`: Set this to a valid User UUID (e.g., from the database) to simulate an authenticated user.
    *   `access_token`: (Optional) If you enable security, place your JWT token here.
    *   `groupId`: Helper variable for group-related requests.

## Routing Strategy

All requests are routed through the **API Gateway** (`localhost:8080`) using the following prefixes:

### Account Service
*   **External URL**: `{{baseUrl}}/studybuddy/account/...`
*   **Internal Service Path**: `/account/...`
*   **Example**: `GET /studybuddy/account/users/me` -> `account-service:8081/account/users/me`

### Collaboration Service
*   **External URL**: `{{baseUrl}}/studybuddy/collab/...`
*   **Internal Service Path**: `/collab/...`
*   **Example**: `GET /studybuddy/collab/api/v1/groups` -> `collaboration-service:8082/collab/api/v1/groups`

> **Note**: The controllers in the microservices have been refactored to include these `/account` and `/collab` prefixes directly. The Gateway simply forwards the request without stripping the prefix (beyond the initial `/studybuddy`).

## Usage Tips

*   **Prerequisites**: Ensure all Docker containers are running (`docker-compose up`).
*   **Environment**: Make sure the `StudyBuddy - Local (Dev)` environment is active in Postman to resolve `{{baseUrl}}`.
