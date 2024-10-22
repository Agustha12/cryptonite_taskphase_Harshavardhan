
---

# **Linux Shell Scripting Challenge Writeup**

This writeup covers several challenges aimed at understanding and manipulating the `PATH` variable in a Linux shell environment. You'll learn how to disrupt existing commands, create your own commands, and control their execution through the `PATH`.

## **1. The PATH Variable**

In this challenge, the goal is to prevent the `/challenge/run` program from deleting a flag file by ensuring it cannot find the `rm` command. The `rm` command is typically located in directories specified by the `PATH` variable, and by manipulating this variable, we can control the execution environment for child processes.

### **Example:**
```bash
hacker@path~the-path-variable:~$ PATH=" "
hacker@path~the-path-variable:~$ /challenge/run  
Trying to remove /flag...  
/challenge/run: line 4: rm: command not found  
The flag is still there! I might as well give it to you!  
pwn.college{wa6y9Vc5glRH68sPyYN4gTdRQ5-.dZzNwUDLyMTN0czW}
```

### **Challenge:**
To complete this challenge, set the `PATH` variable to an empty space so that the `rm` command cannot be found when `/challenge/run` is executed.

---

## **2. Setting PATH**

In this challenge, you need to run the `win` command, which is stored in the `/challenge/more_commands/` directory. Since this directory is not included in the default `PATH`, you will replace the `PATH` variable to include only this directory.

### **Example:**
```bash
hacker@path~setting-path:~$ PATH=/challenge/more_commands/  
hacker@path~setting-path:~$ /challenge/run  
Invoking 'win'....  
Congratulations! You properly set the flag and 'win' has launched!  
pwn.college{wcqrcshv4Fth079NzKVQy3wb-rN.dVzNyUDLyMTN0czW}
```

### **Challenge:**
Modify the `PATH` variable to include the `/challenge/more_commands/` directory, allowing the `win` command to be executed directly.

---

## **3. Adding Commands**

In this challenge, the `win` command needs to be created since it doesn't exist. You can create a shell script called `win`, place it in your home directory, and adjust the `PATH` variable accordingly.

### **Steps:**

1. Create a script called `win`:
   ```bash
   hacker@path~adding-commands:~$ nano win
   ```

2. Add the following line to the `win` script:
   ```bash
   #!/bin/bash
   cat /flag
   ```

3. Make the script executable:
   ```bash
   hacker@path~adding-commands:~$ chmod +x win
   ```

4. Set the `PATH` variable to include your home directory:
   ```bash
   hacker@path~adding-commands:~$ PATH=$PATH:/home/hacker
   ```

5. Execute the `/challenge/run` command:
   ```bash
   hacker@path~adding-commands:~$ /challenge/run  
   Invoking 'win'....  
   pwn.college{Q7jRDI5qBvFA8xXj_SA6BZ7-oUu.dZzNyUDLyMTN0czW}
   ```

### **Challenge:**
Create a command named `win` and ensure it executes correctly when invoked by `/challenge/run`.

---

## **4. Hijacking Commands**

This challenge is similar to the first, where the `/challenge/run` program tries to delete the flag file. The goal is to create a `rm` command that does nothing, effectively hijacking the original `rm` command.

### **Steps:**

1. Create a script called `rm`:
   ```bash
   hacker@path~hijacking-commands:~$ nano rm
   ```

2. Add a line that does nothing (or add a simple echo command for verification):
   ```bash
   #!/bin/bash
   echo "This is a hijacked rm command."
   ```

3. Make the script executable:
   ```bash
   hacker@path~hijacking-commands:~$ chmod +x rm
   ```

4. Update the `PATH` to include your home directory:
   ```bash
   hacker@path~hijacking-commands:~$ PATH=/home/hacker:$PATH
   ```

5. Run the `/challenge/run` command:
   ```bash
   hacker@path~hijacking-commands:~$ /challenge/run  
   Trying to remove /flag...  
   Found 'rm' command at /home/hacker/rm. Executing!  
   pwn.college{0iARKHjz1N2rrLWxPX-NG94KQJI.ddzNyUDLyMTN0czW}
   ```

### **Challenge:**
Create your own `rm` command to intercept the call made by `/challenge/run`.

---

## **Conclusion**

These challenges demonstrated the importance of the `PATH` variable in a Linux environment and how it influences command execution. By manipulating the `PATH`, you can control which commands are available to child processes, allowing for creative solutions in various scenarios. Mastering these techniques will enhance your proficiency in shell scripting and command line operations.

---

