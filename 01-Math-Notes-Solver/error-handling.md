# Math Notes Solver – Error Handling and Input Validation

## 1. Overview

Error handling is an important part of Math Notes Solver.

Users may enter incomplete, invalid or mathematically incorrect expressions. The application needs to identify such cases and prevent incorrect calculations.

The expression-processing engine includes validation and error-handling checks across its processing stages.

## 2. Input Validation

Input validation checks whether the provided mathematical expression can be processed.

The application should consider the following cases:

- Empty input.
- Unsupported characters.
- Missing operands.
- Incorrect operator placement.
- Unbalanced parentheses.
- Invalid mathematical expressions.

For example:

| Input | Issue |
|---|---|
| Empty input | No expression provided |
| `5 +` | Missing operand |
| `* 5 2` | Incorrect operator placement |
| `5 + @` | Unsupported character |
| `(5 + 2` | Unbalanced parentheses |

These examples represent validation cases to handle in the expression-processing pipeline.

## 3. Tokenization Errors

The tokenizer identifies invalid or unsupported characters while converting the input into tokens.

Possible issues include:

- Unexpected characters.
- Invalid number formats.
- Unsupported mathematical symbols.

The tokenizer should report invalid input rather than silently ignoring unsupported characters.

## 4. Parsing Errors

The parser checks whether the generated tokens follow the expected mathematical grammar.

Possible parsing errors include:

- Missing operands.
- Unexpected operators.
- Incorrect expression structure.
- Unbalanced parentheses.
- Incomplete expressions.

For example:

```text
10 + * 5
```

This expression contains consecutive operators without a valid operand between them.

The parser should reject such expressions instead of generating an invalid AST.

## 5. Evaluation Errors

Even when an expression is syntactically valid, mathematical evaluation may produce errors.

### Division by Zero

Example:

```text
10 / 0
```

Division by zero is undefined.

The evaluator should detect this condition and return an appropriate error.

### Invalid Operations

The evaluator should also ensure that operations are performed only on valid operands and supported data types.

## 6. Error Handling Across the Processing Pipeline

The processing stages have different responsibilities:

| Component | Responsibility |
|---|---|
| Input Validation | Check initial user input |
| Tokenizer | Identify invalid tokens |
| Parser | Detect grammatical errors |
| AST Construction | Maintain a valid expression structure |
| Evaluator | Detect invalid mathematical operations |
| Backend | Return appropriate error information |
| Frontend | Display understandable error messages |

## 7. Example Error Scenarios

| Scenario | Expected Behaviour |
|---|---|
| Empty expression | Ask the user to enter an expression |
| Invalid character | Report unsupported input |
| Missing operand | Report an invalid expression |
| Unbalanced parentheses | Report a parsing error |
| Division by zero | Report a mathematical evaluation error |

## 8. Good Error-Handling Practices

A reliable expression-processing application should follow these practices:

**1. Validate Early**

Check user input before beginning expression evaluation.

**2. Separate Error Types**

Keep lexical, parsing and evaluation errors distinguishable.

**3. Provide Meaningful Messages**

Avoid displaying technical stack traces directly to users.

**4. Prevent Invalid Evaluation**

Do not continue evaluation when the expression structure is invalid.

**5. Keep Error Handling Modular**

Separate validation and error-handling responsibilities across the relevant modules.

## 9. Conclusion

Error handling improves the reliability and usability of Math Notes Solver.

By validating input, identifying parsing problems and detecting mathematical errors, the application can process valid expressions while providing useful feedback for invalid ones.
