# 📁 Simple File Management Application

A basic **Python script** providing a command-line interface for fundamental file operations in the current working directory.

-----

## ✨ Features

This script allows you to perform the following file management tasks:

  * **Create** a new file.
  * **View** all files in the current directory.
  * **Delete** an existing file.
  * **Read** the content of a file.
  * **Edit/Append** content to an existing file.

-----

## 🚀 Getting Started

### Prerequisites

You only need **Python 3** installed on your system.

### Installation

No installation is required. Simply save the provided code into a file named (for example) `file_manager.py`.

### Usage

1.  Open your terminal or command prompt.

2.  Navigate to the directory where you saved the file.

3.  Run the script using the following command:

    ```bash
    python file_manager.py
    ```

4.  The application menu will appear, and you can select an option by entering the corresponding number (1-6).

    ```
    FILE MANAGEMENT APP
    1: Create file
    2: View all files
    3: Delete file
    4: Read file
    5: Edit file
    6: Exit
    Enter your choice(1-6) =
    ```

-----

## 🔧 Code Overview

The script is built around several functions, each handling a specific file operation:

| Function | Description |
| :--- | :--- |
| `create_file(filename)` | Creates a new file. *(Note: The file-opening mode 'X' attempts to create the file exclusively; it fails if the file already exists.)* |
| `view_all_files()` | Lists all files and directories in the current working directory using `os.listdir()`. |
| `delete_file(filename)` | Deletes the specified file using `os.remove()`. |
| `read_file(filename)` | Reads and prints the entire content of a file. *(Note: The implementation currently uses `'sample.txt'` as the hardcoded file name to read, regardless of the input `filename`.)* |
| `edit_file(filename)` | Appends new data to the end of a file. *(Note: The implementation currently uses `'sample.txt'` as the hardcoded file name to edit, regardless of the input `filename`.)* |
| `main()` | The main application loop that displays the menu and handles user input. |

-----

## 🐛 Issues and Potential Improvements

  * **Hardcoded File Names in Read/Edit:** The functions `read_file` and `edit_file` currently **hardcode** the file name to `'sample.txt'`, meaning they will operate on `'sample.txt'` regardless of the filename the user enters.
  * **Error Handling for `create_file`:** The original code attempts to use `'X'` as the file mode, which is Python's exclusive creation mode. If the file exists, this correctly raises a `FileExistsError`. However, the error handling logic is slightly simplified and could be clearer.
  * **Input Validation:** The `main` function lacks input validation to ensure the user enters a number between 1 and 6.

### Suggested Correction for `read_file` and `edit_file`

To fix the hardcoded file issue, replace `'sample.txt'` with the `filename` variable within the `with open(...)` statements in both `read_file` and `edit_file`:

**Before (Example from `read_file`):**

```python
with open('sample.txt', 'r') as f:
```

**After (Correction):**

```python
with open(filename, 'r') as f:
```