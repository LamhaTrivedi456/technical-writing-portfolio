# Math Notes Solver – Technical Documentation

## 1. Introduction

Math Notes Solver is a mathematical expression-processing application inspired by the mathematical solving experience of Apple Math Notes.

The application allows users to enter mathematical expressions and obtain calculated results along with step-by-step explanations.

The main objective of this project is to understand how mathematical expressions can be processed programmatically using parsing techniques, tree-based representations, and expression evaluation.

The system combines a user-friendly frontend with a Java Spring Boot backend to process mathematical input and return structured calculation results.

## 2. Problem Statement

Evaluating mathematical expressions requires more than performing basic arithmetic operations.

A system must understand:
- Mathematical operators and operands.
- Operator precedence and associativity.
- Parentheses and nested expressions.
- Valid and invalid mathematical expressions.
- The correct order of operations.

Simply evaluating an expression from left to right can produce incorrect results.

For example:

```text
10 + 5 * 2
```

The correct result is:

```text
20
```

Multiplication must be performed before addition.

Math Notes Solver addresses this problem through a structured expression-processing pipeline.

## 3. Objectives

The primary objectives are:

- Accept mathematical expressions through a frontend interface.
- Process expressions using a custom parsing engine.
- Apply mathematical operator precedence and associativity.
- Generate an Abstract Syntax Tree (AST).
- Evaluate expressions using post-order traversal.
- Display step-by-step calculations.
- Support linear equation solving.
- Integrate the frontend with a Java Spring Boot backend.

## 4. Technology Stack

| Component | Technology |
|---|---|
| Frontend | Project frontend interface |
| Backend | Java, Spring Boot |
| Expression Processing | Custom Parsing Engine |
| Data Structure | Abstract Syntax Tree |
| Parsing | Tokenization and Recursive-Descent Parsing |
| Evaluation | Post-order Tree Traversal |
| Communication | REST API |

## 5. System Architecture

The application follows a frontend-backend architecture.

The frontend is responsible for accepting mathematical input and presenting the calculated output.

The Spring Boot backend receives the expression, processes it through the mathematical parsing engine, and returns the result and calculation steps.

### Processing Workflow

```text
          USER
            |
            v
     FRONTEND INTERFACE
            |
            v
       SPRING BOOT
          BACKEND
            |
            v
       INPUT VALIDATION
            |
            v
         TOKENIZER
            |
            v
     RECURSIVE-DESCENT
          PARSER
            |
            v
     ABSTRACT SYNTAX
           TREE
            |
            v
      POST-ORDER
       EVALUATION
            |
            v
     CALCULATION STEPS
        AND RESULT
            |
            v
      FRONTEND DISPLAY
```

## 6. How the Expression Processing Works

The mathematical processing engine follows multiple stages.

### 6.1 Input Handling

The user enters a mathematical expression through the frontend.

Example:

```text
10 + 5 * 2
```

The expression is sent to the backend for processing.

### 6.2 Tokenization

Tokenization converts the input expression into smaller meaningful units called tokens.

For example:

```text
Input:
10 + 5 * 2

Tokens:
10, +, 5, *, 2
```

The tokenizer identifies numbers and mathematical operators so that the parser can process them.

### 6.3 Recursive-Descent Parsing

After tokenization, the parser analyzes the expression according to mathematical grammar and operator precedence.

Recursive-descent parsing uses multiple parsing functions to recognize different parts of an expression.

It helps handle:
- Addition and subtraction.
- Multiplication and division.
- Parentheses.
- Nested mathematical expressions.
- Operator precedence.

This ensures that the expression is interpreted correctly rather than simply evaluated from left to right.

### 6.4 Abstract Syntax Tree (AST)

An Abstract Syntax Tree represents a mathematical expression in a hierarchical tree structure.

For example:

```text
Expression:
10 + 5 * 2
```

Its tree representation is:

```text
          +
         / \
       10   *
           / \
          5   2
```

The root node represents the addition operation.

The multiplication operation becomes the right child because it has higher precedence.

The AST makes it easier to evaluate expressions in the correct order.

### 6.5 Post-order Traversal

Once the AST is constructed, the evaluator processes it using post-order traversal.

Post-order traversal follows this sequence:

1. Visit the left subtree.
2. Visit the right subtree.
3. Process the root node.

For the previous expression:

```text
10 + 5 * 2
```

The evaluation sequence is:

```text
5 * 2 = 10
10 + 10 = 20
```

Final Result:

```text
20
```

This approach ensures that child expressions are evaluated before their parent operators.

### 6.6 Step-by-Step Calculation Generation

The application provides intermediate calculation steps instead of displaying only the final answer.

For example:

```text
Expression: 10 + 5 * 2

Step 1: 5 * 2 = 10

Step 2: 10 + 10 = 20

Final Answer: 20
```

This helps users understand how the result was obtained.

## 7. Linear Equation Solving

Apart from arithmetic expression evaluation, the application also supports linear equation solving.

A linear equation contains a variable whose highest power is one.

Example:

```text
2x + 4 = 10
```

The solving process involves isolating the variable.

```text
2x + 4 = 10

2x = 10 - 4

2x = 6

x = 6 / 2

x = 3
```

The application presents the solution through step-by-step calculations.

**Current Scope:** The implemented equation-solving functionality focuses on supported linear equations. Quadratic and higher-degree equation solving are not currently included.

## 8. Frontend and Backend Integration

The application uses a frontend-backend communication model.

### Frontend Responsibilities

- Accept mathematical expressions.
- Send input to the backend.
- Display calculation results.
- Present step-by-step explanations.
- Provide an interface for interacting with the application.

### Backend Responsibilities

- Receive requests through Spring Boot.
- Validate mathematical input.
- Process expressions using the parsing engine.
- Construct the Abstract Syntax Tree.
- Evaluate mathematical expressions.
- Generate calculation steps.
- Return structured results to the frontend.

The frontend and backend communicate through REST API integration.

## 9. Error Handling

Mathematical expressions may contain invalid input or unsupported operations.

The application needs to handle cases such as:

- Invalid mathematical syntax.
- Missing operands.
- Unmatched parentheses.
- Division by zero.
- Unsupported mathematical expressions.

Input validation and error handling help prevent incorrect calculations and improve the reliability of the application.

## 10. Why Use an Abstract Syntax Tree?

An Abstract Syntax Tree provides a structured representation of mathematical expressions.

Its advantages include:

- Represents operator precedence naturally.
- Makes expression evaluation easier.
- Supports recursive processing.
- Separates parsing from evaluation.
- Makes it easier to extend the expression engine.

It also provides a foundation for adding more mathematical operations in the future.

## 11. Challenges and Learning Outcomes

During the development of this project, several important programming concepts were explored.

### Challenges

- Understanding operator precedence and associativity.
- Converting mathematical input into meaningful tokens.
- Designing a parser for mathematical expressions.
- Constructing a correct AST.
- Evaluating expressions in the correct order.
- Generating meaningful calculation steps.
- Integrating the processing engine with the frontend through Spring Boot.

### Learning Outcomes

This project provided practical experience with:

- Parsing techniques and expression evaluation.
- Recursive algorithms.
- Tree data structures.
- Post-order traversal.
- Backend development using Spring Boot.
- REST API integration.
- Modular software design.
- Translating mathematical logic into software functionality.

## 12. Future Enhancements

The application can be extended with additional mathematical capabilities.

Possible improvements include:

- Quadratic equation solving.
- Polynomial expression evaluation.
- Trigonometric functions.
- Logarithmic and exponential calculations.
- Support for more complex mathematical expressions.
- Improved mathematical error messages.
- More detailed calculation explanations.
- Handwriting recognition for mathematical input.

These enhancements would expand the application beyond basic arithmetic and supported linear equations.

## 13. Conclusion

Math Notes Solver demonstrates how mathematical expressions can be processed through tokenization, parsing, tree construction, and evaluation.

By combining a frontend interface with a Java Spring Boot backend and a custom expression-processing engine, the application provides calculated results along with step-by-step explanations.

The project helped develop a deeper understanding of parsing algorithms, abstract syntax trees, recursive processing, and backend integration.

It also demonstrates how fundamental computer science concepts can be applied to build practical software applications.

---

**Project:** Math Notes Solver  
**Author:** Lamha Trivedi  
**Focus Areas:** Java, Spring Boot, Parsing Algorithms, AST, Expression Evaluation, REST APIs
