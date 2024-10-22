


---

# Permissions Challenges Walkthrough

This repository contains a series of challenges centered around Linux file permissions. Below is an explanation of each challenge, the commands used, and how they help understand file ownership, groups, and permissions in Unix-based systems.

## 1. Changing File Ownership

The `chown` command is used to change the ownership of a file. Normally, only the `root` user can do this, but in this challenge, the `hacker` user has been granted the ability to use `chown` freely. The goal is to change the ownership of the `/flag` file to `hacker` and read its contents.

### Steps:
1. Create a file and directory:
    ```bash
    mkdir pwn_directory
    touch college_file
    ```

2. Check current ownership using `ls -l`:
    ```bash
    ls -l
    ```

3. Change the owner of the file:
    ```bash
    chown hacker college_file
    ```

4. Change the ownership of `/flag`:
    ```bash
    chown hacker /flag
    ```

5. Read the flag:
    ```bash
    cat /flag
    ```

**Command Recap:**
- `chown [user] [file]`: Changes file ownership.

---

## 2. Groups and Files

The `chgrp` command allows you to change the group ownership of files. In this challenge, you need to change the group ownership of the `/flag` file from `root` to `hacker` so you can read the flag.

### Steps:
1. Check the current group ownership:
    ```bash
    ls -l /flag
    ```

2. Change the group ownership:
    ```bash
    chgrp hacker /flag
    ```

3. Read the flag:
    ```bash
    cat /flag
    ```

**Command Recap:**
- `chgrp [group] [file]`: Changes the group ownership of a file.

---

## 3. Fun with Group Names

In this challenge, the group name for the `hacker` user has been randomized. You must use the `id` command to find out which group you belong to and then change the group ownership of the `/flag` file.

### Steps:
1. Find the current group:
    ```bash
    id
    ```

2. Change the group ownership of `/flag`:
    ```bash
    chgrp [group_name] /flag
    ```

3. Read the flag:
    ```bash
    cat /flag
    ```

**Command Recap:**
- `id`: Shows the user's UID, GID, and groups.
- `chgrp [group] [file]`: Changes the group ownership of a file.

---

## 4. Changing Permissions

Here, you need to change the file permissions of the `/flag` file using `chmod`. Although the file is owned by `root`, the challenge grants the `hacker` user all-powerful `chmod` capabilities, allowing you to modify any file permissions.

### Steps:
1. Check the current file permissions:
    ```bash
    ls -l /flag
    ```

2. Change the permissions to allow read, write, and execute access for all:
    ```bash
    chmod ugo+rwx /flag
    ```

3. Read the flag:
    ```bash
    cat /flag
    ```

**Command Recap:**
- `chmod ugo+rwx [file]`: Grants read, write, and execute permissions to the user (u), group (g), and others (o).

---

## 5. Executable Files

In this challenge, the `/challenge/run` file needs to be executable to get the flag. You must modify the file's permissions to allow execution.

### Steps:
1. Check the current permissions of `/challenge/run`:
    ```bash
    ls -l /challenge/run
    ```

2. Add execute permissions for all users:
    ```bash
    chmod ugo+x /challenge/run
    ```

3. Run the executable to get the flag:
    ```bash
    /challenge/run
    ```

**Command Recap:**
- `chmod ugo+x [file]`: Adds execute permissions for user, group, and others.

Certainly! Here's a writeup of the permission-tweaking and SUID bit challenge you completed:

---

## 6. Challenge: Permission Tweaking Practice

This challenge is designed to help you practice changing file permissions in Linux using the `chmod` command. You are tasked with modifying the permissions of the `/challenge/pwn` file eight times in a row based on the required conditions. If you succeed in all eight rounds, you earn the ability to modify and access the `/flag` file to obtain the final flag.

---

### **Step-by-Step Breakdown**

#### **Round 0: Changing permissions to `rw-------`**

- Current: `rw-r--r--`
- Needed: `rw-------`

Command:
```bash
chmod go-r /challenge/pwn
```

#### **Round 1: Changing permissions to `rwxrwxrwx`**

- Current: `rw-------`
- Needed: `rwxrwxrwx`

Command:
```bash
chmod ugo+rwx /challenge/pwn
```

#### **Round 2: Changing permissions to `r--rwxrwx`**

- Current: `rwxrwxrwx`
- Needed: `r--rwxrwx`

Command:
```bash
chmod u-wx /challenge/pwn
```

#### **Round 3: Changing permissions to `----w--w-`**

- Current: `r--rwxrwx`
- Needed: `----w--w-`

Command:
```bash
chmod ugo-rx /challenge/pwn
```

#### **Round 4: Changing permissions to `--x-wx-w-`**

- Current: `----w--w-`
- Needed: `--x-wx-w-`

Command:
```bash
chmod ug+x /challenge/pwn
```

#### **Round 5: Changing permissions to `--xrwxrwx`**

- Current: `--x-wx-w-`
- Needed: `--xrwxrwx`

Command:
```bash
chmod go+rx /challenge/pwn
```

#### **Round 6: Changing permissions to `r-xrwxrwx`**

- Current: `--xrwxrwx`
- Needed: `r-xrwxrwx`

Command:
```bash
chmod u+r /challenge/pwn
```

#### **Round 7: Changing permissions to `r--rwxrwx`**

- Current: `r-xrwxrwx`
- Needed: `r--rwxrwx`

Command:
```bash
chmod u-x /challenge/pwn
```

---

After solving all eight rounds correctly, the ownership of the `/flag` file changes so that you can modify its permissions.

#### **Accessing the `/flag` file**

The `/flag` file initially has no read, write, or execute permissions for anyone. To read it, you need to make it readable.

Command:
```bash
chmod ugo+r /flag
```

Finally, retrieve the flag using:
```bash
cat /flag
```

The flag is:
```
pwn.college{oC-Pl2KvLO5LpPVdqcJi6-e16d0.dBTM2QDLyMTN0czW}
```

---

## Challenge 7: Permissions Setting Practice

In this extended practice, you need to use `chmod` to both remove and add permissions, as well as overwrite permissions altogether.

#### **Round 0: Changing permissions to `r---w---x`**

Command:
```bash
chmod u=r,g=w,o=x /challenge/pwn
```

#### **Round 1: Changing permissions to `-w--wx--x`**

Command:
```bash
chmod u=w,g=wx,o=x /challenge/pwn
```

#### **Round 2: Changing permissions to `rwxr---wx`**

Command:
```bash
chmod u=rwx,g=r,o=wx /challenge/pwn
```

#### **Round 3: Changing permissions to `-wx----w-`**

Command:
```bash
chmod u=wx,g=-,o=w /challenge/pwn
```

#### **Round 4: Changing permissions to `r-x-w--w-`**

Command:
```bash
chmod u=rx,g=w,o=w /challenge/pwn
```

#### **Round 5: Changing permissions to `--xr-x-wx`**

Command:
```bash
chmod u=x,g=rx,o=wx /challenge/pwn
```

#### **Round 6: Changing permissions to `rwx--x-wx`**

Command:
```bash
chmod u=rwx,g=x,o=wx /challenge/pwn
```

#### **Round 7: Changing permissions to `----w-r--`**

Command:
```bash
chmod u=-,g=w,o=r /challenge/pwn
```

After completing the eight rounds, the permissions of the `/flag` file are set, and you can make it readable:

```bash
chmod ugo+r /flag
```

Retrieve the final flag using:
```bash
cat /flag
```

The flag is:
```
pwn.college{AYggQoEDjIea595t5L8cDqwG4v9.dNTM5QDLyMTN0czW}
```

---

## Challenge 8: The SUID Bit

In this challenge, you use the SUID bit to execute a program (`/challenge/getroot`) as the `root` user. This allows you to gain root access and read the flag.

First, check the current permissions of the `/challenge/getroot` program:
```bash
ls -l /challenge/getroot
```

The program is owned by `root`, but doesn't have the SUID bit set yet.

To set the SUID bit, use:
```bash
chmod u+s /challenge/getroot
```

Now, execute the program to gain root privileges and read the flag:
```bash
/challenge/getroot
cat /flag
```

Flag retrieved:
```
pwn.college{random_flag_string}
```

---

## **Key Concepts**

- **`chmod` command**: Used to change file permissions.
- **Permission symbols**: `r` (read), `w` (write), `x` (execute), and `-` (no permission).
- **Chaining permissions**: `chmod` allows setting different permissions for user, group, and others using commas.
- **SUID bit**: This special bit allows a program to run with the file owner’s permissions, enabling privilege escalation.

By understanding how to manipulate file permissions, including SUID, you can control access in Linux systems effectively.

--- 

