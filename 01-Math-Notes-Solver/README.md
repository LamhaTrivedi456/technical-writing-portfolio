# Math Notes Solver
### Mathematical Expression Processing and Step-by-Step Calculation

**Developed by Lamha Trivedi**

## Overview

Math Notes Solver is a mathematical expression-processing application inspired by Apple Math Notes.

The application allows users to enter mathematical expressions, process them through a structured evaluation pipeline, and view step-by-step calculations along with the final result.

The project combines frontend development, Spring Boot backend integration, parsing techniques, and tree-based data structures to demonstrate how mathematical expressions can be processed programmatically.

## Key Features

- Interactive frontend for entering mathematical expressions.
- Expression processing through a structured backend.
- Tokenization of mathematical expressions.
- Recursive-descent parsing.
- Abstract Syntax Tree (AST) construction.
- Post-order tree traversal for expression evaluation.
- Step-by-step calculation generation.
- Mathematical expression validation and error handling.
- Frontend and Spring Boot backend integration.

## How It Works

The application follows a structured expression-processing workflow:

1. **User Input:** The user enters a mathematical expression.
2. **Tokenization:** The input is divided into meaningful tokens.
3. **Parsing:** Tokens are analysed according to mathematical grammar rules.
4. **AST Construction:** An Abstract Syntax Tree represents the expression structure.
5. **Evaluation:** The AST is evaluated using post-order traversal.
6. **Calculation Steps:** Intermediate operations are generated.
7. **Result Display:** The frontend displays the calculations and final result.

## System Architecture

```text
        User Input
            |
            v
      Frontend UI
            |
            v
    Spring Boot Backend
            |
            v
        Tokenizer
            |
            v
 Recursive-Descent Parser
            |
            v
     Abstract Syntax Tree
            |
            v
   Post-order Evaluation
            |
            v
   Step-by-Step Results
            |
            v
      Frontend UI
```

## Technical Stack

| Component | Technology |
|---|---|
| Programming Language | Java |
| Backend Framework | Spring Boot |
| API Communication | REST APIs |
| Expression Parsing | Recursive-Descent Parsing |
| Data Structure | Abstract Syntax Tree |
| Evaluation | Post-order Traversal |
| Frontend | Project frontend framework |

## Documentation

The following documents explain the technical implementation and engineering concepts behind the project.

| Document | Description |
|---|---|
| [System Architecture](./architecture.md) | Explains the application architecture and component interactions. |
| [Technical Documentation](./documentation.md) | Describes the project implementation and processing workflow. |
| [Algorithms](./algorithms.md) | Explains tokenization, parsing, AST construction, and evaluation. |
| [API Documentation](./api-documentation.md) | Describes frontend-backend communication and API examples. |
| [Error Handling](./error-handling.md) | Covers input validation and error scenarios. |

## Engineering Concepts Demonstrated

- Object-oriented programming.
- Data structures and algorithms.
- Expression parsing and evaluation.
- Operator precedence and associativity.
- Tree traversal techniques.
- REST API integration.
- Modular software design.
- Input validation and error handling.

## Future Enhancements

Potential areas for improvement include:

- Support for quadratic and polynomial equations.
- Trigonometric and logarithmic expressions.
- More advanced equation-solving capabilities.
- Improved mathematical input handling.
- Enhanced calculation visualization.

## About the Developer

**Lamha Trivedi**

Computer Science Engineering Student | Software Developer | GenAI Enthusiast

I enjoy building practical software applications and understanding the engineering concepts behind them. This project reflects my interest in algorithms, backend development, and making complex mathematical operations easier to understand.

- [LinkedIn](https://linkedin.com/in/lamha-trivedi)
- [GitHub](https://github.com/LamhaTrivedi456)
- Email: lamhatrivedi546@gmail.com

---

*Building software, understanding the engineering behind it, and making technology easier to understand.*
