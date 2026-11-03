# Algorithms and Expression Processing

## 1. Introduction

Math Notes Solver processes mathematical expressions using tokenization, parsing, tree construction and expression evaluation.

The main objective is to understand the structure of a mathematical expression, respect operator precedence and generate step-by-step calculations.

This document explains the core algorithms used in the expression-processing engine.

## 2. Tokenization

Tokenization is the first stage of expression processing.

It converts an input expression into smaller meaningful units called tokens.

For example:

**Input:**
```text
12 + 5 * 2
```

**Generated tokens:**

| Token | Type |
|---|---|
| 12 | Number |
| + | Operator |
| 5 | Number |
| * | Operator |
| 2 | Number |

The tokenizer identifies numbers, operators and other supported symbols.

**Why is tokenization important?**

- Makes expressions easier to process.
- Separates numbers and operators.
- Helps identify invalid characters.
- Provides structured input for the parser.

## 3. Parsing

Parsing determines how tokens are related according to mathematical grammar rules.

Math Notes Solver uses a recursive-descent parsing approach.

The parser analyses the expression and constructs a structured representation while respecting operator precedence and associativity.

For example:

```text
2 + 3 * 4
```

Multiplication has higher precedence than addition.

Therefore, the expression is interpreted as:

```text
2 + (3 * 4)
```

The parser helps ensure that mathematical expressions are interpreted correctly.

## 4. Abstract Syntax Tree (AST)

An Abstract Syntax Tree represents the hierarchical structure of an expression.

Consider:

```text
2 + 3 * 4
```

Its AST can be represented as:

```text
       +
      / \
     2   *
        / \
       3   4
```

Here:

- The root node represents addition.
- The left child represents the number 2.
- The right child represents multiplication.
- The multiplication node contains 3 and 4.

**Benefits of using an AST:**

- Represents expression structure clearly.
- Maintains operator precedence.
- Separates parsing from evaluation.
- Makes expression processing easier to extend.

## 5. Post-order Traversal

Post-order traversal is used to evaluate the generated AST.

It follows this order:

1. Visit the left subtree.
2. Visit the right subtree.
3. Process the current node.

For the expression:

```text
2 + 3 * 4
```

The evaluation order is:

```text
3 * 4 = 12
2 + 12 = 14
```

Final result:

```text
14
```

**Why post-order traversal?**

An operator node should be evaluated only after its operands have been evaluated.

Post-order traversal naturally provides this execution order.

## 6. Step-by-Step Calculation Generation

The evaluator can record intermediate operations while processing the expression tree.

For example:

Expression:
```text
10 + 2 * 5
```

Calculation steps:

```text
Step 1: 2 * 5 = 10
Step 2: 10 + 10 = 20
Final Result: 20
```

This makes the application more understandable than simply displaying the final answer.

## 7. Overall Processing Pipeline

```text
Mathematical Expression
          |
          v
      Tokenizer
          |
          v
        Tokens
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
 Intermediate Calculations
          |
          v
      Final Result
```

## 8. Complexity Considerations

Let n represent the number of tokens in an expression.

| Operation | Expected Time Complexity |
|---|---|
| Tokenization | O(n) |
| AST Construction | O(n) |
| AST Traversal | O(n) |
| Expression Evaluation | O(n) |

The above complexities assume that each token and AST node is processed a constant number of times.

The AST requires O(n) space in the worst case.

## 9. Conclusion

The combination of tokenization, recursive-descent parsing, AST construction and post-order traversal provides a structured approach to mathematical expression processing.

Each stage has a separate responsibility, making the application easier to understand, maintain and extend.
