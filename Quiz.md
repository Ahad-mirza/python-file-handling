# File Handling Problems with Error Handling

### ❓ **Problem 1: Writing Data to a File (with Error Handling)**
**Problem:**  
You need to write a list of strings into a file. If the file already exists, it should append the new data to the file. If there’s an error (like permission denied), the program should handle it gracefully.

💡 **Hint:** Use `try-except` to handle file-related errors.

---

### ❓ **Problem 2: Counting Lines in a File (with Error Handling)**
**Problem:**  
You need to count the number of lines in a file. If the file doesn’t exist, it should print an error message.

💡 **Hint:** Use `try-except` to catch errors like `FileNotFoundError`.

---

### ❓ **Problem 3: Reading Data from a CSV File (with Error Handling)**
**Problem:**  
You need to read a CSV file, process its content, and handle potential errors such as malformed CSV files or missing files.

💡 **Hint:** Use `try-except` to handle errors, and consider using Python's `csv` module.

---

### ❓ **Problem 4: Appending to a Log File (with Error Handling)**
**Problem:**  
You need to append a log entry to a log file. If the file doesn't exist, it should create a new one. If there’s a permission issue, it should report the error.

💡 **Hint:** Use `try-except` to handle errors during file opening or writing.

---

### ❓ **Problem 5: Moving a File (with Error Handling)**
**Problem:**  
You need to move a file from one directory to another. If the file doesn't exist, or if the destination directory doesn't exist, it should print an error message.

💡 **Hint:** Use `shutil.move()` for file movement and handle errors with `try-except`.

---
