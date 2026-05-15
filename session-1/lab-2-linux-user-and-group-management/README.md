# Lab 2 - Linux User and Group Management
## lab screen 
<img width="1106" height="607" alt="Screenshot 2026-05-10 152451" src="https://github.com/user-attachments/assets/c8e37eec-9347-47c8-8540-7c7a5edd2bc5" />

## Objectives

- Create and manage Linux users
- Set and modify user passwords
- Configure sudo permissions
- Create and manage groups
- Modify primary and supplementary groups
- Rename users
- Delete users from the system

---

# Lab Tasks

## Step 1 - Create `user1` and `user2`

### Commands

```bash
sudo useradd user1
```

```bash
sudo useradd user2
```

### Explanation

Creates two new users:
- user1
- user2

### Expected Output

```bash
No output
```

---

## Step 2 - Set Passwords for Both Users

### Commands

```bash
sudo passwd user1
```

```bash
sudo passwd user2
```

### Explanation

Assigns passwords to both users.

### Expected Output

```bash
New password:
Retype new password:
passwd: all authentication tokens updated successfully.
```

---

## Step 3 - Permit `user1` to Run All Commands Using sudo

### Command

```bash
sudo usermod -aG wheel user1
```

### Explanation

Adds `user1` to the `wheel` group.

On RHEL systems, members of the `wheel` group can execute sudo commands.

### Verification

```bash
id user1
```

### Expected Output

```bash
uid=1001(user1) gid=1001(user1) groups=1001(user1),10(wheel)
```

---

## Step 4 - Permit `user2` to Run sudo Commands Without Password

### Command

```bash
sudo visudo
```

### Add the Following Line

```bash
user2 ALL=(ALL) NOPASSWD: ALL
```

### Explanation

Allows `user2` to execute sudo commands without entering a password.

### Expected Output

```bash
No output
```

---

## Step 5 - Create Group `server`

### Command

```bash
sudo groupadd server
```

### Explanation

Creates a new group named `server`.

### Expected Output

```bash
No output
```

---

## Step 6 - Add `user2` to `server` as a Supplementary Group

### Command

```bash
sudo usermod -aG server user2
```

### Explanation

Adds `user2` to the supplementary group `server`.

### Verification

```bash
id user2
```

### Expected Output

```bash
uid=1002(user2) gid=1002(user2) groups=1002(user2),1003(server)
```

---

## Step 7 - Change the Primary Group of `user1` to `web`

### Step 7.1 - Create `web` Group

### Command

```bash
sudo groupadd web
```

### Explanation

Creates a new group named `web`.

---

### Step 7.2 - Change Primary Group

### Command

```bash
sudo usermod -g web user1
```

### Explanation

Changes the primary group of `user1` to `web`.

### Verification

```bash
id user1
```

### Expected Output

```bash
uid=1001(user1) gid=1004(web) groups=1004(web),10(wheel)
```

---

## Step 8 - Rename `user1` to `Ali`

### Command

```bash
sudo usermod -l Ali user1
```

### Explanation

Changes the username from:
- user1 → Ali

### Expected Output

```bash
No output
```

---

## Step 9 - Change Password for `Ali`

### Command

```bash
sudo passwd Ali
```

### Explanation

Changes the password for the renamed user.

### Expected Output

```bash
New password:
Retype new password:
passwd: all authentication tokens updated successfully.
```

---

## Step 10 - Delete `Ali` from the System

### Command

```bash
sudo userdel Ali
```

### Explanation

Deletes the user account from the system.

### Expected Output

```bash
No output
```

---

# Verification Commands

## Display User Information

```bash
id user2
```

```bash
id Ali
```

---

## Check Groups

```bash
cat /etc/group
```

---

## Check Users

```bash
cat /etc/passwd
```

---

# Notes

- `useradd` creates new users.
- `passwd` sets or changes passwords.
- `groupadd` creates new groups.
- `usermod` modifies user properties.
- `-aG` adds a user to supplementary groups.
- `-g` changes the primary group.
- `wheel` group grants sudo access on RHEL systems.
- `visudo` safely edits the sudoers file.
- `userdel` deletes users from the system.
- Always use `visudo` instead of editing `/etc/sudoers` directly.
