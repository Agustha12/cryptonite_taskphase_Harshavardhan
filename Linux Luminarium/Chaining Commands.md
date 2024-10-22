



---

# **Linux Shell Scripting Challenge Writeup**

This writeup details several challenges designed to help you understand basic shell scripting concepts in a Linux environment. You'll learn how to chain commands, create and execute shell scripts, redirect outputs, and make scripts executable.

## **1. Chaining with Semicolons**

Chaining commands is a fundamental skill in shell scripting, allowing you to run multiple commands in one line using the semicolon (`;`). This method can streamline your workflow by eliminating the need for multiple lines of input.

### **Example:**

You can run commands sequentially:
```bash
hacker@dojo:~$ echo COLLEGE > pwn; cat pwn
COLLEGE
```

### **Challenge:**
In this challenge, you need to run `/challenge/pwn` and `/challenge/college` by chaining them with a semicolon.

### **Solution:**
```bash
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn;/challenge/college  
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:  
pwn.college{IG-ob3pRZHLG2MYD6qhu3schntZ.dVTN4QDLyMTN0czW}
```

---

## **2. Your First Shell Scripts**

A shell script is a file containing a series of commands that can be executed together. You can create a script to run multiple commands without entering them individually.

### **Example:**
```bash
hacker@dojo:~$ bash pwn.sh
COLLEGE
```

### **Challenge:**
Create a script named `x.sh` to run `/challenge/pwn` and `/challenge/college`.

### **Solution:**
1. Create the script:
   ```bash
   hacker@chaining~your-first-shell-script:~$ nano x.sh
   ```

2. Add the following lines to `x.sh`:
   ```bash
   #!/bin/bash
   /challenge/pwn
   /challenge/college
   ```

3. Execute the script:
   ```bash
   hacker@chaining~your-first-shell-script:~$ bash x.sh  
   Great job, you've written your first shell script! Here is the flag:  
   pwn.college{0a1-Wr5BOyTdpmHLDRQCwuQoShq.dFzN4QDLyMTN0czW}
   ```

---

## **3. Redirecting Script Output**

You can redirect the output of a script to another command, allowing for efficient data handling.

### **Example:**
```bash
hacker@dojo:~$ echo PWN; echo COLLEGE > output
hacker@dojo:~$ cat output
PWN
COLLEGE
```

### **Challenge:**
Create a script that calls `/challenge/pwn` and `/challenge/college`, piping its output into `/challenge/solve`.

### **Solution:**
1. Create the script:
   ```bash
   hacker@chaining~redirecting-script-output:~$ nano x.sh
   ```

2. Add the following lines to `x.sh`:
   ```bash
   #!/bin/bash
   /challenge/pwn
   /challenge/college
   ```

3. Execute the script with piping:
   ```bash
   hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve  
   Correct! Here is your flag:  
   pwn.college{MAIqN8SIX9bDQShY169AaBr_oQk.dhTM5QDLyMTN0czW}
   ```

---

## **4. Executable Shell Scripts**

Making your shell script executable allows you to run it without explicitly calling `bash`.

### **Example:**
To make a script executable, use the `chmod` command:
```bash
hacker@chaining~executable-shell-scripts:~$ chmod ugo+x s.sh
```

### **Challenge:**
Create an executable shell script that invokes `/challenge/solve`.

### **Solution:**
1. Create the script:
   ```bash
   hacker@chaining~executable-shell-scripts:~$ nano s.sh
   ```

2. Add the following line to `s.sh`:
   ```bash
   #!/bin/bash
   /challenge/solve
   ```

3. Make it executable:
   ```bash
   hacker@chaining~executable-shell-scripts:~$ chmod ugo+x s.sh
   ```

4. Run the script:
   ```bash
   hacker@chaining~executable-shell-scripts:~$ ./s.sh  
   Congratulations on your shell script execution! Your flag:  
   pwn.college{U-A_sj-mpSn4eoZiAOaFM7P4qGP.dRzNyUDLyMTN0czW}
   ```

---

## **Conclusion**

This series of challenges introduced you to essential shell scripting techniques, including chaining commands, creating and executing scripts, redirecting output, and setting file permissions. Mastering these skills will greatly enhance your efficiency and capability in navigating a Linux environment.

---
