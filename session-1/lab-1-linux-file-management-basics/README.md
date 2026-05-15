# Lab 1 - Linux File Management Basics


## lab screen 
<img width="971" height="598" alt="image" src="https://github.com/user-attachments/assets/48d9f862-2d9b-4e32-a0d1-4e65cc4a1f8d" />

## Objectives
- Display system date and time
- Count lines and words in files
- Display the beginning and end of files
- Create directories and subdirectories
- Create, move, copy, and delete files
- Work with hard links and symbolic links
- Practice Linux file management commands

---

# Lab Tasks

## Step 1 - Display Current Date and Time

### Command

```bash
date
```

### Explanation

Displays the current system date and time.

### Expected Output

```bash
Thu May 15 06:30:00 PM EEST 2026
```

---

## Step 2 - Count Lines and Words in `/etc/group`

### Command

```bash
wc /etc/group
```

### Explanation

Displays:
- Number of lines
- Number of words
- Number of characters
- File name

### Expected Output

```bash
75 75 1200 /etc/group
```

> Output may vary from one system to another.

---

## Step 3 - Display the First 10 Lines of `/etc/group`

### Command

```bash
head -10 /etc/group
```

### Explanation

Displays the first 10 lines of the file.

### Expected Output

```bash
root:x:0:
daemon:x:1:
bin:x:2:
...
```

---

## Step 4 - Display the Last 10 Lines of `/etc/group`

### Command

```bash
tail -10 /etc/group
```

### Explanation

Displays the last 10 lines of the file.

### Expected Output

```bash
ssh_keys:x:998:
mosad:x:1000:
...
```

---

## Step 5 - Create Three Directories

### Command

```bash
mkdir dir1 dir2 dir3
```

### Explanation

Creates three directories in the current working directory.

### Expected Output

```bash
No output
```

---

## Step 6 - Create Subdirectories

### Command

```bash
mkdir dir1/subdir1 dir2/subdir2 dir3/subdir3
```

### Explanation

Creates one subdirectory inside each directory.

### Expected Output

```bash
No output
```

---

## Step 7 - Create Three Files

### Command

```bash
touch file1 file2 file3
```

### Explanation

Creates three empty files.

### Expected Output

```bash
No output
```

---

## Step 8 - Move `file1` to `subdir1`

### Command

```bash
mv file1 dir1/subdir1/
```

### Explanation

Moves `file1` into `subdir1`.

### Expected Output

```bash
No output
```

---

## Step 9 - Copy `file2` to `subdir2`

### Command

```bash
cp file2 dir2/subdir2/
```

### Explanation

Copies `file2` into `subdir2`.

### Expected Output

```bash
No output
```

---

## Step 10 - List Content of `dir2` and `subdir2`

### Commands

```bash
ls dir2
```

```bash
ls dir2/subdir2
```

### Explanation

Displays the contents of:
- `dir2`
- `subdir2`

### Expected Output

```bash
subdir2
```

```bash
file2
```

---

## Step 11 - Copy Files to `subdir3`

### Command

```bash
cp dir1/subdir1/file1 file2 file3 dir3/subdir3/
```

### Explanation

Copies:
- file1
- file2
- file3

into `subdir3`.

### Expected Output

```bash
No output
```

---

## Step 12 - List Content of `subdir3`

### Command

```bash
ls dir3/subdir3
```

### Explanation

Displays all files inside `subdir3`.

### Expected Output

```bash
file1  file2  file3
```

---

## Step 13 - Delete `subdir3`

### Command

```bash
rm -r dir3/subdir3
```

### Explanation

Deletes the subdirectory recursively.

### Expected Output

```bash
No output
```

---

## Step 14 - Create a Hard Link for `/etc/group`

### Command

```bash
ln /etc/group dir2/subdir2/group_hard
```

### Explanation

Creates a hard link for `/etc/group` inside `subdir2`.

### Expected Output

```bash
No output
```

---

## Step 15 - Create a Symbolic Link for `file1`

### Command

```bash
ln -s ~/linux-system-administration-bootcamp/dir1/subdir1/file1 dir2/subdir2/file1_soft
```

### Explanation

Creates a symbolic (soft) link for `file1`.

### Expected Output

```bash
No output
```

---

## Step 16 - List Content of `subdir2`

### Command

```bash
ls -l dir2/subdir2
```

### Explanation

Displays detailed information about:
- file2
- hard link
- symbolic link

### Expected Output

```bash
-rw-r--r-- 1 user user    0 file2
-rw-r--r-- 2 root root 1200 group_hard
lrwxrwxrwx 1 user user   25 file1_soft -> /home/user/dir1/subdir1/file1
```

---

## Step 17 - Create `/Documents/test/new/secret`

### Commands

```bash
mkdir -p Documents/test/new
```

```bash
touch Documents/test/new/secret
```

### Explanation

Creates nested directories and an empty file named `secret`.

### Expected Output

```bash
No output
```

---

## Step 18 - Move `secret` to `subdir2`

### Command

```bash
mv Documents/test/new/secret dir2/subdir2/
```

### Explanation

Moves the `secret` file into `subdir2`.

### Expected Output

```bash
No output
```

---

# Final Structure Verification

### Command

```bash
tree
```

### Expected Output

```bash
.
├── dir1
│   └── subdir1
│       └── file1
├── dir2
│   └── subdir2
│       ├── file2
│       ├── file1_soft
│       ├── group_hard
│       └── secret
├── dir3
├── file2
└── file3
```

---

# Notes

- `mv` is used to move files and directories.
- `cp` is used to copy files and directories.
- `ln` creates hard links by default.
- `ln -s` creates symbolic (soft) links.
- Hard links reference the same inode.
- Soft links point to the file path.
- `mkdir -p` creates parent directories automatically.
- `head` displays the beginning of a file.
- `tail` displays the end of a file.
- `wc` counts lines, words, and characters.
