# 📁 Assignment 1 — Basic Linux Commands

> **FileManager.sh** — A Bash utility to manage files and directories using basic Linux commands only.  
> ⚠️ **Note:** Do NOT use the `sed` command. Use only basic Linux commands.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Part 1 — Directory Management](#part-1--directory-management)
- [Part 2 — File Management](#part-2--file-management)
- [Command Reference](#command-reference)
- [Usage Snapshots](#usage-snapshots)

---

## Overview

Create a shell utility `FileManager.sh` that handles both **directory** and **file** operations via simple command-line arguments.

```bash
./FileManager.sh <command> <arguments>
```

Make it executable:
```bash
chmod +x FileManager.sh
```

---

## Part 1 — Directory Management

The script must support the following directory operations:

| Command | Description |
|---|---|
| `addDir` | Create a new directory |
| `deleteDir` | Delete an existing directory |
| `listFiles` | List only files in a directory |
| `listDirs` | List only subdirectories in a directory |
| `listAll` | List all contents (files + directories) |

### 📸 Snapshot — Directory Operations

```bash
# Create directories
./FileManager.sh addDir /tmp dir1
./FileManager.sh addDir /tmp dir2
./FileManager.sh addDir /tmp dir3
```
**Output:**
```
Directory '/tmp/dir1' created successfully.
Directory '/tmp/dir2' created successfully.
Directory '/tmp/dir3' created successfully.
```

---

```bash
# List only files in /tmp
./FileManager.sh listFiles /tmp
```
**Output:**
```
Files in /tmp:
  file1.txt
  example.log
```

---

```bash
# List only directories in /tmp
./FileManager.sh listDirs /tmp
```
**Output:**
```
Directories in /tmp:
  dir1
  dir2
  dir3
```

---

```bash
# List all contents in /tmp
./FileManager.sh listAll /tmp
```
**Output:**
```
All contents in /tmp:
  dir1/
  dir2/
  dir3/
  file1.txt
  example.log
```

---

```bash
# Delete a directory
./FileManager.sh deleteDir /tmp dir3
```
**Output:**
```
Directory '/tmp/dir3' deleted successfully.
```

---

## Part 2 — File Management

Extend `FileManager.sh` to also handle file operations:

| Command | Description |
|---|---|
| `addFile` | Create a file (optionally with initial content) |
| `addContentToFile` | Append content to end of file |
| `addContentToFileBegining` | Add content to beginning of file |
| `showFileBeginingContent` | Show top N lines of a file |
| `showFileEndContent` | Show last N lines of a file |
| `showFileContentAtLine` | Show content at a specific line number |
| `showFileContentForLineRange` | Show content for a line number range |
| `moveFile` | Move or rename a file |
| `copyFile` | Copy a file to another location |
| `clearFileContent` | Clear all content from a file |
| `deleteFile` | Delete a file |

### 📸 Snapshot — File Operations

```bash
# Create an empty file
./FileManager.sh addFile /tmp/dir1 file1.txt
```
**Output:**
```
File '/tmp/dir1/file1.txt' created successfully.
```

---

```bash
# Create a file with initial content
./FileManager.sh addFile /tmp/dir1 file1.txt "Initial Content"
```
**Output:**
```
File '/tmp/dir1/file1.txt' created with content: "Initial Content"
```

---

```bash
# Append content to end of file
./FileManager.sh addContentToFile /tmp/dir1 file1.txt "Additional Content"
```
**Output:**
```
Content appended to '/tmp/dir1/file1.txt'.
```

---

```bash
# Add content to beginning of file
./FileManager.sh addContentToFileBegining /tmp/dir1 file1.txt "Prepended Content"
```
**Output:**
```
Content added to beginning of '/tmp/dir1/file1.txt'.
```

---

```bash
# Show first 5 lines of file
./FileManager.sh showFileBeginingContent /tmp/dir1 file1.txt 5
```
**Output:**
```
Top 5 lines of '/tmp/dir1/file1.txt':
Prepended Content
Initial Content
Additional Content
Line 4...
Line 5...
```

---

```bash
# Show last 5 lines of file
./FileManager.sh showFileEndContent /tmp/dir1 file1.txt 5
```
**Output:**
```
Last 5 lines of '/tmp/dir1/file1.txt':
Line 6...
Line 7...
Line 8...
Line 9...
Additional Content
```

---

```bash
# Show content at line 10
./FileManager.sh showFileContentAtLine /tmp/dir1 file1.txt 10
```
**Output:**
```
Line 10 of '/tmp/dir1/file1.txt':
Content at line ten
```

---

```bash
# Show content from line 5 to 10
./FileManager.sh showFileContentForLineRange /tmp/dir1 file1.txt 5 10
```
**Output:**
```
Lines 5–10 of '/tmp/dir1/file1.txt':
Line 5 content
Line 6 content
Line 7 content
Line 8 content
Line 9 content
Line 10 content
```

---

```bash
# Rename a file (move within same directory)
./FileManager.sh moveFile /tmp/dir1/file1.txt /tmp/dir1/file2.txt

# Move file to another directory
./FileManager.sh moveFile /tmp/dir1/file2.txt /tmp/dir2/
```
**Output:**
```
File moved/renamed to '/tmp/dir1/file2.txt'.
File moved to '/tmp/dir2/'.
```

---

```bash
# Copy file to another directory
./FileManager.sh copyFile /tmp/dir2/file2.txt /tmp/dir1/

# Copy and rename
./FileManager.sh copyFile /tmp/dir1/file2.txt /tmp/dir1/file3.txt
```
**Output:**
```
File copied to '/tmp/dir1/'.
File copied as '/tmp/dir1/file3.txt'.
```

---

```bash
# Clear all content from a file (keeps the file)
./FileManager.sh clearFileContent /tmp/dir1 file3.txt
```
**Output:**
```
Content of '/tmp/dir1/file3.txt' cleared successfully.
```

---

```bash
# Delete a file
./FileManager.sh deleteFile /tmp/dir1 file2.txt
```
**Output:**
```
File '/tmp/dir1/file2.txt' deleted successfully.
```

---

## Command Reference

### Directory Commands

```
./FileManager.sh addDir      <path> <dirName>
./FileManager.sh deleteDir   <path> <dirName>
./FileManager.sh listFiles   <path>
./FileManager.sh listDirs    <path>
./FileManager.sh listAll     <path>
```

### File Commands

```
./FileManager.sh addFile                    <path> <fileName> [content]
./FileManager.sh addContentToFile           <path> <fileName> <content>
./FileManager.sh addContentToFileBegining   <path> <fileName> <content>
./FileManager.sh showFileBeginingContent    <path> <fileName> <n>
./FileManager.sh showFileEndContent         <path> <fileName> <n>
./FileManager.sh showFileContentAtLine      <path> <fileName> <lineNo>
./FileManager.sh showFileContentForLineRange <path> <fileName> <start> <end>
./FileManager.sh moveFile                   <source> <destination>
./FileManager.sh copyFile                   <source> <destination>
./FileManager.sh clearFileContent           <path> <fileName>
./FileManager.sh deleteFile                 <path> <fileName>
```

---

## Linux Commands Used

| Operation | Linux Command |
|---|---|
| Create directory | `mkdir` |
| Delete directory | `rm -r` |
| List files only | `find <path> -maxdepth 1 -type f` |
| List dirs only | `find <path> -maxdepth 1 -type d` |
| List all | `ls` |
| Create file | `touch` |
| Write content | `echo "..." > file` |
| Append content | `echo "..." >> file` |
| Prepend content | `cat` + temp file |
| Show top N lines | `head -n` |
| Show last N lines | `tail -n` |
| Show specific line | `awk 'NR==n'` |
| Show line range | `awk 'NR>=s && NR<=e'` |
| Move/Rename | `mv` |
| Copy | `cp` |
| Clear file | `> file` or `truncate -s 0` |
| Delete file | `rm` |

> ⚠️ **Constraint:** `sed` command is NOT allowed. Use only the commands listed above.

---

*Assignment 1 — Basic Linux Commands*
