# Python Automation – Developer Guide

## 1. Introduction

Python is a general-purpose programming language widely used for scripting, automation, data processing and application development.

Automation involves using programs to perform repetitive tasks with minimal manual intervention.

Python is particularly useful for automation because of its readable syntax, built-in libraries and extensive ecosystem.

## 2. What Is Python Automation?

Python automation means writing scripts that perform routine operations automatically.

Examples include:

- Organizing files into folders.
- Renaming multiple files.
- Reading and writing text files.
- Processing CSV data.
- Generating reports.
- Performing repetitive calculations.

## 3. Setting Up the Environment

### Install Python

Download Python from:

https://www.python.org/downloads/

Verify the installation:

```bash
python --version
```

### Create a Project Folder

```bash
mkdir python-automation
cd python-automation
```

### Create a Python File

```bash
touch main.py
```

On Windows, you can create the file directly in VS Code or use:

```bash
type nul > main.py
```

## 4. Understanding Python Scripts

A Python script is a file containing instructions that the interpreter executes.

Example:

```python
def greet(name):
    return f"Hello, {name}!"

message = greet("Developer")
print(message)
```

Output:

```text
Hello, Developer!
```

Functions help organize reusable logic and reduce code duplication.

## 5. Working with Files

Python provides the built-in `os` and `pathlib` modules for file and directory operations.

Example:

```python
from pathlib import Path

folder = Path("documents")

folder.mkdir(exist_ok=True)

print("Directory created successfully")
```

Using `pathlib` makes filesystem operations easier to read and maintain.

## 6. Reading and Writing Files

Python provides file handling through the `open()` function.

Example:

```python
with open("notes.txt", "w") as file:
    file.write("Python automation guide")
```

Reading the file:

```python
with open("notes.txt", "r") as file:
    content = file.read()

print(content)
```

The `with` statement automatically manages file closure.

## 7. Functions and Reusable Modules

Functions allow developers to divide a program into smaller tasks.

Example:

```python
def calculate_total(price, quantity):
    return price * quantity

total = calculate_total(100, 3)

print(total)
```

Modules allow related functions to be organized and reused across different Python files.

## 8. Exception Handling

Automation scripts should handle unexpected situations.

Python provides `try`, `except` and `finally` for exception handling.

Example:

```python
try:
    with open("data.txt", "r") as file:
        content = file.read()

except FileNotFoundError:
    print("File not found.")

finally:
    print("Operation completed.")
```

Exception handling helps prevent unexpected failures from terminating a workflow without useful feedback.

## 9. Running Python Scripts

Run a Python script using:

```bash
python main.py
```

For a project with multiple files, organize the code into modules and import the required functions.

## 10. Best Practices

- Use meaningful variable and function names.
- Divide large scripts into smaller functions.
- Handle exceptions appropriately.
- Avoid hardcoding unnecessary file paths.
- Use pathlib for filesystem operations.
- Add comments where they improve understanding.
- Test scripts using different input conditions.

## 11. Conclusion

Python automation provides a practical way to reduce repetitive work and improve productivity.

By combining functions, file handling, modules and exception handling, developers can create reusable scripts for everyday tasks.
