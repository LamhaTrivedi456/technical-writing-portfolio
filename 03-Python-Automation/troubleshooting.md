# Python Automation – Troubleshooting Guide

## 1. Introduction

Python scripts may encounter errors due to incorrect input, missing files, invalid paths or environment configuration.

This guide explains common problems and their solutions.

## 2. Python Command Not Found

**Problem:**

```text
'python' is not recognized as an internal or external command
```

**Possible Cause:**

Python is not installed or its executable directory is not available in the system PATH.

**Solution:**

1. Install Python.
2. Enable the option to add Python to PATH during installation.
3. Restart the terminal.
4. Verify using:

```bash
python --version
```

On Windows, you can also try:

```bash
py --version
```

## 3. FileNotFoundError

**Problem:**

```text
FileNotFoundError
```

**Possible Cause:**

The requested file does not exist at the specified location.

**Solution:**

- Verify the filename.
- Check the directory path.
- Use pathlib to inspect file locations.
- Handle missing files using try-except.

## 4. PermissionError

**Problem:**

```text
PermissionError
```

**Possible Cause:**

The script does not have permission to access or modify a particular file.

**Solution:**

- Check file permissions.
- Close applications that may be locking the file.
- Use an appropriate directory.
- Avoid unnecessary administrator privileges.

## 5. ModuleNotFoundError

**Problem:**

```text
ModuleNotFoundError
```

**Possible Cause:**

The required module is not installed or the script is running in a different Python environment.

**Solution:**

For third-party packages, install the required dependency:

```bash
python -m pip install package_name
```

Verify that the correct Python interpreter is selected.

## 6. IndentationError

**Problem:**

```text
IndentationError
```

**Possible Cause:**

Python uses indentation to define code blocks. Incorrect spacing can cause this error.

**Solution:**

- Use consistent indentation.
- Prefer four spaces.
- Check loops, functions and conditional statements.

## 7. Debugging Best Practices

- Read the complete error traceback.
- Identify the line where the error occurred.
- Check input values and file paths.
- Use print statements for simple debugging.
- Use a debugger for complex workflows.
- Test with valid and invalid inputs.

## 8. Conclusion

Understanding common Python errors helps developers diagnose issues and build more reliable automation scripts.

Good troubleshooting practices improve maintainability and reduce unnecessary debugging time.
