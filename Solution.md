# File Handling Problems with Error Handling - Solutions

---

### ❓ **Problem 1: Writing Data to a File (with Error Handling)**

**Problem:**  
You need to write a list of strings into a file. If the file already exists, it should append the new data to the file. If there’s an error (like permission denied), the program should handle it gracefully.

💡 **Hint:** Use `try-except` to handle file-related errors.

#### 📝 **Solution:**

```python
data = ["Hello", "Welcome to file handling!", "Python makes it easy."]
file_name = "output.txt"

try:
    with open(file_name, 'a') as file:  # 'a' mode appends data to the file
        for line in data:
            file.write(line + "\n")
    print(f"Data successfully written to {file_name}.")
except PermissionError:
    print(f"Error: Permission denied to write to {file_name}.")
except Exception as e:
    print(f"An unexpected error occurred: {e}")
```
Explanation:
This code uses `try-except` to handle errors while writing to a file. If the file already exists, the data is appended to it. If there is a permission issue, it catches the `PermissionError`. If any other unexpected error occurs, it’s captured by the generic Exception block.

---

# Problem 2: Counting Lines in a File (with Error Handling)

### ❓ **Problem:**  
You need to count the number of lines in a file. If the file doesn’t exist, it should print an error message.

💡 **Hint:** Use `try-except` to catch errors like `FileNotFoundError`.

---

### 📝 **Solution:**

```python
file_name = "example.txt"

try:
    with open(file_name, 'r') as file:
        lines = file.readlines()
        print(f"The file has {len(lines)} lines.")
except FileNotFoundError:
    print(f"Error: The file '{file_name}' was not found.")
except Exception as e:
    print(f"An unexpected error occurred: {e}")
```
**💬 Explanation**:
This code opens the file in read mode `('r')`. If the file is not found, it handles the FileNotFoundError. Any other errors that might occur, such as permission issues or corrupted files, are handled by the generic Exception block.

- The `open()` function opens the file for reading.
- The `readlines()` method reads all the lines from the file into a list.
- The length of the list is used to count the number of lines in the file.
- If the file does not exist, it raises a `FileNotFoundError`, which is caught and reported.
- Any other unexpected error is caught using the Exception block and displayed.

---
# Problem 3: Reading Data from a CSV File (with Error Handling)

### ❓ **Problem:**  
You need to read a CSV file, process its content, and handle potential errors such as malformed CSV files or missing files.

💡 **Hint:** Use `try-except` to handle errors, and consider using Python's `csv` module.

---

### 📝 **Solution:**

```python
import csv

file_name = 'data.csv'

try:
    with open(file_name, 'r') as file:
        reader = csv.reader(file)
        for row in reader:
            print(row)  # Printing each row in the CSV file
except FileNotFoundError:
    print(f"Error: The file '{file_name}' does not exist.")
except csv.Error:
    print(f"Error: The file '{file_name}' is not a valid CSV file.")
except Exception as e:
    print(f"An unexpected error occurred: {e}")
```
**💬 Explanation**:
This solution reads data from a `CSV` file using the csv.reader. It handles errors such as:

- `FileNotFoundError`: If the file is not found, it displays an appropriate error message.
- `csv.Error`: If the file is not a valid CSV file, this error will be triggered.
- Any other unexpected errors are caught by the generic `Exception` block.
**Key Points:**
The `csv.reader` is used to read each row from the CSV file.
The `open()` function opens the file in read mode ('r').
The try-except block ensures that various potential errors (file not found, malformed CSV) are handled gracefully.

---
# Problem 4: Appending to a Log File (with Error Handling)

### ❓ **Problem:**  
You need to append a log entry to a log file. If the file doesn't exist, it should create a new one. If there’s a permission issue, it should report the error.

💡 **Hint:** Use `try-except` to handle errors during file opening or writing.

---

### 📝 **Solution:**

```python
log_entry = "2024-12-23 12:00:00 - Log entry created successfully."
log_file = 'logfile.txt'

try:
    with open(log_file, 'a') as file:
        file.write(log_entry + "\n")
    print(f"Log entry added to {log_file}.")
except PermissionError:
    print(f"Error: Permission denied to write to {log_file}.")
except Exception as e:
    print(f"An unexpected error occurred: {e}")
```
**💬 Explanation:**
This solution appends a log entry to the file using append mode ('a').

- If the file already exists, the new data will be added at the end without overwriting the existing content.
- If there is a permission issue, the program will catch the PermissionError and notify the user.
- Any other unexpected errors are caught by the generic Exception block.
**Key Points:**
- The file is opened in append mode ('a'), which means data is added without erasing existing content.
- The `try-except` block handles **permission issues** and other potential file-related errors.
- The log entry includes the current date and time for easy tracking of when it was added.

---

# Problem 5: Moving a File (with Error Handling)

### ❓ **Problem:**  
You need to move a file from one directory to another. If the file doesn't exist, or if the destination directory doesn't exist, it should print an error message.

💡 **Hint:** Use `shutil.move()` for file movement and handle errors with try-except.

---

### 📝 **Solution:**

```python
import shutil
import os

source_file = 'source.txt'
destination_dir = 'destination_folder/'

# Check if source file exists
if not os.path.exists(source_file):
    print(f"Error: The file '{source_file}' does not exist.")
else:
    try:
        # Ensure the destination directory exists
        os.makedirs(destination_dir, exist_ok=True)
        
        # Move the file
        shutil.move(source_file, os.path.join(destination_dir, os.path.basename(source_file)))
        print(f"File moved to {destination_dir}.")
    except PermissionError:
        print(f"Error: Permission denied to move the file.")
    except Exception as e:
        print(f"An unexpected error occurred: {e}")
```
### 💬 **Explanation:**  
This solution moves a file from one directory to another with error handling:

- **Check if the source file exists:**  
  Before attempting to move the file, the code checks if the source file exists using `os.path.exists()`. If the file doesn't exist, it prints an error message.

- **Create destination directory if necessary:**  
  It uses `os.makedirs()` to create the destination directory if it doesn't already exist. The `exist_ok=True` flag ensures that no error occurs if the directory already exists.

- **Move the file:**  
  The file is moved using `shutil.move()`, which moves the file to the destination directory.

- **Handle errors:**
  - **PermissionError:** If there’s a permission issue (e.g., lacking permission to access the file or the destination directory), the program handles it and prints a relevant message.
  - **Other unexpected errors:** Any other errors are caught by the generic `Exception` block.

---

### 📝 **Key Points:**
- `shutil.move()` is used to move the file to the destination directory.
- The code handles **file existence checks** and **directory creation**.
- **Error handling** is done for both permission issues and other unexpected errors.
