# Python Automation – Practical Code Examples

This document contains practical Python examples that demonstrate common automation tasks.

## 1. Create Multiple Folders

```python
from pathlib import Path

folders = ["Images", "Documents", "Videos"]

for folder in folders:
    Path(folder).mkdir(exist_ok=True)

print("Folders created successfully")
```

**Explanation:** Creates multiple directories using a loop and pathlib.

## 2. Rename Multiple Files

```python
from pathlib import Path

folder = Path("files")

for index, file in enumerate(folder.iterdir()):
    if file.is_file():
        new_name = folder / f"file_{index}{file.suffix}"
        file.rename(new_name)

print("Files renamed successfully")
```

**Explanation:** Iterates through files and assigns new names while preserving file extensions.

Run this example only on a test folder because it changes filenames.

## 3. Count Words in a Text File

```python
from pathlib import Path

file_path = Path("sample.txt")

text = file_path.read_text(encoding="utf-8")

word_count = len(text.split())

print("Total words:", word_count)
```

**Explanation:** Reads a text file and counts its whitespace-separated words.

## 4. Process CSV Files

```python
import csv

with open("students.csv", "r", newline="", encoding="utf-8") as file:
    reader = csv.DictReader(file)

    for row in reader:
        print(row)
```

**Explanation:** Reads CSV records as dictionaries, making column-based access easier.

## 5. Handle Missing Files

```python
from pathlib import Path

file_path = Path("report.txt")

try:
    content = file_path.read_text(encoding="utf-8")
    print(content)

except FileNotFoundError:
    print("The requested file does not exist.")
```

**Explanation:** Handles missing-file errors without an unhandled exception.

## 6. Generate a Simple Report

```python
from datetime import datetime

report = f"""
Automation Report
Generated: {datetime.now()}

Status: Completed
"""

with open("report.txt", "w", encoding="utf-8") as file:
    file.write(report)

print("Report generated")
```

**Explanation:** Generates a basic report containing the current date and time.

## Conclusion

These examples demonstrate how Python's standard library can automate everyday tasks involving directories, files, CSV data and reports.

Each script can be extended to handle larger workflows and more complex requirements.
