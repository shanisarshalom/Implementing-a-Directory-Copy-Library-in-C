# Directory Copy Library in C

This project involves implementing a C library that provides functionality similar to Python's `shutil.copytree`. The library enables recursive copying of directory trees, including files, subdirectories, symbolic links, and file permissions, based on user-specified flags.

---

## Objective

To develop a robust C library for copying directories and files that supports:
- **Recursive directory traversal**.
- **Handling of symbolic links**.
- **Preservation of file permissions**.
- **Comprehensive error handling with resource cleanup**.

---

## Features

- **File Copying**:
  - Copy individual files, with options for handling symbolic links and preserving permissions.
  
- **Directory Copying**:
  - Recursively copy the contents of directories and subdirectories.
  
- **Symbolic Link Handling**:
  - Copy symbolic links as links or copy the content they point to.

- **Permissions**:
  - Optionally preserve file permissions during the copying process.

- **Error Reporting**:
  - Use `perror` to handle and report errors effectively.

---

## Project Structure

### Files

1. **`copytree.h`**:
   - Provides function declarations for copying files and directories.
   - Includes symbolic link and permission handling flags.

2. **`copytree.c`**:
   - Implements the file and directory copying functionality.
   - Includes helper functions for error handling and resource cleanup.

3. **`main.c`**:
   - A sample program that demonstrates how to use the library.
   - Handles command-line arguments for source, destination, and flags.

---

## Usage
 
  ### Compilation
 
  1. Compile the library:
     ```bash
     gcc -c copytree.c -o copytree.o
     ar rcs libcopytree.a copytree.o
     ```
 
  2. Compile the main program:
     ```bash
     gcc main.c -L. -lcopytree -o main_program
     ```
 
  ### Running the Program
 
  Run the program with source and destination directories, and optional flags:
 
     ```bash
     ./main_program [-l] [-p] <source_directory> <destination_directory>
     ```
 
  ### Command-Line Options
 
  - **`-l`**: Copy symbolic links as links (instead of the content they point to).
  - **`-p`**: Preserve file permissions during copying.
 
  ### Example Commands

  1. Copy directory structure without symbolic link or permission handling:
     ```bash
     ./main_program source_directory destination_directory
     ```
 
  2. Copy directory structure with symbolic link and permission handling:
     ```bash
     ./main_program -l -p source_directory destination_directory
     ```
 
  ---
 
  ## Testing
 
  ### Sample Directory Structure
 
  Create the following test structure under `source_directory`:
 
  ```
  source_directory/
  ├── file1.txt
  ├── file2.txt
  ├── subdir1/
  │   ├── file3.txt
  │   └── file4.txt
  └── subdir2/
      ├── file5.txt
      └── link_to_file1 -> ../file1.txt
  ```
 
  ### Expected Output
 
  After running the program, `destination_directory` should mirror the structure of `source_directory`:
 
  ```
  destination_directory/
  ├── file1.txt
  ├── file2.txt
  ├── subdir1/
  │   ├── file3.txt
  │   └── file4.txt
  └── subdir2/
      ├── file5.txt
      └── link_to_file1 -> ../file1.txt
  ```
 /
