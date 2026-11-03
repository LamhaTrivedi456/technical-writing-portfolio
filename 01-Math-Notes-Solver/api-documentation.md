# Math Notes Solver – API Documentation

## 1. Overview

Math Notes Solver uses a Spring Boot backend to process mathematical expressions and communicate results to the frontend.

The backend acts as the communication layer between the user interface and the expression-processing engine.

This document describes the API integration approach, example request structure and expected response format.

**Note:** The endpoint and JSON structures below are illustrative documentation examples. Replace them with the actual endpoint names and DTO fields implemented in the project before publishing.

## 2. API Architecture

The API follows a request-response model.

The general workflow is:

1. The frontend collects a mathematical expression.
2. The expression is sent to the Spring Boot backend.
3. The backend validates the request.
4. The expression-processing engine processes the input.
5. The backend prepares the response.
6. The frontend displays the result and calculation steps.

## 3. Example API Endpoint

### Solve Mathematical Expression

| Property | Description |
|---|---|
| Method | POST |
| Example endpoint | `/api/solve` |
| Content-Type | `application/json` |
| Purpose | Process a mathematical expression |

### Example Request

```http
POST /api/solve
Content-Type: application/json
```

```json
{
  "expression": "10 + 2 * 5"
}
```

### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| expression | String | Mathematical expression entered by the user |

### Example Successful Response

```json
{
  "success": true,
  "expression": "10 + 2 * 5",
  "steps": [
    "2 * 5 = 10",
    "10 + 10 = 20"
  ],
  "result": 20
}
```

### Response Fields

| Field | Type | Description |
|---|---|---|
| success | Boolean | Indicates whether processing succeeded |
| expression | String | Original mathematical expression |
| steps | Array | Intermediate calculation steps |
| result | Number | Final calculated result |

The exact response structure should match the backend implementation.

## 4. Frontend and Backend Integration

The frontend communicates with the Spring Boot backend using HTTP requests.

The integration process involves:

- Collecting user input.
- Sending the expression to the backend.
- Receiving the processed response.
- Extracting intermediate calculation steps.
- Displaying the final result.

The frontend and backend are kept separate so that expression-processing logic can be maintained independently of the user interface.

## 5. Example Request Flow

```text
User
 |
 v
Frontend
 |
 | HTTP POST Request
 v
Spring Boot Controller
 |
 v
Request Validation
 |
 v
Expression Processing Service
 |
 v
Expression Evaluator
 |
 v
Response Generation
 |
 | HTTP Response
 v
Frontend Result Display
```

## 6. API Error Responses

The backend should return meaningful error responses when an expression cannot be processed.

For example, an illustrative error response could be:

```json
{
  "success": false,
  "message": "Division by zero is not allowed."
}
```

Error responses should clearly communicate what went wrong without exposing internal implementation details.

## 7. API Design Considerations

The API integration should follow these principles:

- Use appropriate HTTP methods.
- Validate incoming requests.
- Return structured JSON responses.
- Separate controller and business logic.
- Handle invalid input consistently.
- Keep error messages understandable.
- Avoid exposing internal implementation details.

## 8. Conclusion

The Spring Boot integration allows the frontend to communicate with the mathematical expression-processing engine through a structured API.

This separation improves maintainability and allows the expression-processing logic to evolve independently of the frontend.
