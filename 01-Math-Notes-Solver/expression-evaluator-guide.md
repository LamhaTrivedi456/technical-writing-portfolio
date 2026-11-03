# How an Expression Evaluator Works: From Tokens to Abstract Syntax Trees

## 1. Introduction

Have you ever wondered how a calculator understands an expression such as:

```text
10 + 5 * 2
```

A computer does not simply read mathematical expressions the way humans do. It needs a structured process to identify numbers, understand operators, determine their precedence, and perform calculations in the correct order.

An expression evaluator solves this problem by transforming mathematical input into a structure that a program can understand and evaluate.

In this article, we will explore the key stages involved in building an expression evaluator, using concepts from compiler design and data structures.

## 2. Understanding the Problem

Consider the expression:

```text
10 + 5 * 2
```

The expected result is 20, not 30.

This is because multiplication has higher precedence than addition.

A reliable expression evaluator must understand:
- Numbers and operators.
- Operator precedence.
- Operator associativity.
- Parentheses.
- Valid and invalid expressions.

To achieve this, the expression is processed through multiple stages.

## 3. Stage One: Tokenization

Tokenization is the process of breaking an expression into smaller meaningful units called tokens.

For example:

**Input:**

```text
10 + 5 * 2
```

**Tokens:**

```text
10, +, 5, *, 2
```

Each token has a specific meaning.

| Token | Type |
|---|---|
| 10 | Number |
| + | Operator |
| 5 | Number |
| * | Operator |
| 2 | Number |

Tokenization makes the expression easier for the parser to process.

Without tokenization, the program would need to repeatedly interpret raw characters while evaluating the expression.

## 4. Stage Two: Parsing

After tokenization, the expression needs to be analysed.

Parsing determines how the different tokens are connected and which operations should be performed first.

One approach is recursive-descent parsing.

A recursive-descent parser uses grammar rules and functions to understand the structure of an expression.

For example:

```text
10 + 5 * 2
```

The parser recognises that multiplication has higher precedence than addition.

Therefore, the expression is interpreted as:

```text
10 + (5 * 2)
```

This ensures that mathematical rules are followed correctly.

## 5. Stage Three: Abstract Syntax Tree

An Abstract Syntax Tree (AST) represents an expression as a hierarchical tree.

Consider:

```text
10 + 5 * 2
```

Its AST looks like this:

```text
        +
       / \
     10   *
         / \
        5   2
```

The tree represents the logical structure of the expression.

The addition operator is the root node, while multiplication is represented as its right child.

This structure makes it possible to evaluate the expression without repeatedly checking operator precedence.

### Why use an AST?

An AST provides several advantages:

- Represents mathematical expressions hierarchically.
- Preserves operator precedence.
- Separates parsing from evaluation.
- Makes complex expressions easier to process.
- Supports future extensions.

## 6. Stage Four: Evaluating the AST

Once the AST has been generated, the expression can be evaluated.

A useful approach is post-order traversal.

Post-order traversal follows three steps:

1. Visit the left subtree.
2. Visit the right subtree.
3. Process the current node.

For our example:

```text
10 + 5 * 2
```

The evaluator first processes the multiplication node.

```text
5 * 2 = 10
```

Then it evaluates the root addition operation.

```text
10 + 10 = 20
```

**Final Result:**

```text
20
```

Post-order traversal is useful because the operands are evaluated before their parent operator.

## 7. Generating Step-by-Step Calculations

An expression evaluator can do more than return a final answer.

It can also record intermediate operations during evaluation.

For example:

**Expression:**

```text
8 + 4 * 3
```

**Calculation steps:**

```text
Step 1: 4 * 3 = 12
Step 2: 8 + 12 = 20
```

**Final Answer: 20**

Recording these operations makes the application more transparent and helps users understand how the result was obtained.

## 8. Handling Invalid Expressions

A reliable evaluator must also handle invalid input.

Consider the following examples:

| Expression | Problem |
|---|---|
| `5 +` | Missing operand |
| `* 4 2` | Incorrect operator placement |
| `(5 + 2` | Unbalanced parentheses |
| `10 / 0` | Division by zero |

Different stages are responsible for identifying different problems.

- Tokenizer: identifies invalid characters.
- Parser: identifies grammatical errors.
- Evaluator: identifies invalid mathematical operations.

Separating these responsibilities makes the application easier to maintain.

## 9. Understanding Time Complexity

Let n represent the number of tokens in an expression.

For a typical implementation:

| Operation | Time Complexity |
|---|---|
| Tokenization | O(n) |
| AST Construction | O(n) |
| Tree Traversal | O(n) |
| Expression Evaluation | O(n) |

Each token and tree node is processed a constant number of times.

The AST requires O(n) auxiliary space in the worst case.

Actual parsing complexity depends on the grammar and implementation.

## 10. Why This Approach Is Useful

The same concepts used in a mathematical expression evaluator are also relevant to:

- Programming language interpreters.
- Compilers.
- Query processors.
- Spreadsheet formula engines.
- Mathematical software.
- Expression-based automation systems.

Understanding tokenization, parsing and tree traversal provides a foundation for building systems that interpret structured input.

## 11. Conclusion

Building an expression evaluator involves much more than performing arithmetic operations.

It requires transforming raw input into tokens, understanding grammatical structure, constructing an Abstract Syntax Tree and evaluating that tree in the correct order.

These concepts demonstrate how compiler-design techniques and data structures can be applied to practical software applications.

---

**Author:** Lamha Trivedi

Computer Science Engineering Student | Software Developer | GenAI Enthusiast

[LinkedIn](https://linkedin.com/in/lamha-trivedi) | [GitHub](https://github.com/LamhaTrivedi456)
