
---

## Table of Contents

1. [Introduction to Variables in Bash](#introduction-to-variables-in-bash)
2. [Challenge 1: Printing Variables](#challenge-1-printing-variables)
3. [Challenge 2: Setting Variables](#challenge-2-setting-variables)
4. [Challenge 3: Multi-word Variables](#challenge-3-multi-word-variables)
5. [Challenge 4: Exporting Variables](#challenge-4-exporting-variables)
6. [Challenge 5: Printing Exported Variables](#challenge-5-printing-exported-variables)
7. [Challenge 6: Storing Command Output in Variables](#challenge-6-storing-command-output-in-variables)
8. [Challenge 7: Reading Input from the User](#challenge-7-reading-input-from-the-user)
9. [Challenge 8: Reading Files into Variables](#challenge-8-reading-files-into-variables)
10. [Conclusion](#conclusion)

---

## Introduction to Variables in Bash

In **Bash scripting**, variables are an essential concept. Variables allow you to store and manipulate data, making scripts dynamic and reusable. Variables can hold text, numbers, the output of commands, and more.

### Key Points:
- **Variable Declaration:** In Bash, you declare a variable by assigning it a value using the `=` sign (no spaces).
  ```bash
  VAR_NAME=value
  ```
- **Accessing Variables:** To retrieve the value stored in a variable, you prefix the variable name with a `$`.
  ```bash
  echo $VAR_NAME
  ```

- **Exporting Variables:** Variables can be made available to child processes by exporting them.
  ```bash
  export VAR_NAME
  ```

- **Quoting Variables:** To handle multi-word strings, you need to use quotes (`" "` or `' '`).

With this foundation, let's explore each challenge step-by-step.

---

## Challenge 1: Printing Variables

In this challenge, we start with a simple task: printing the value of a predefined variable.

### Problem:
- You are given a variable called `FLAG`. Your task is to print its contents to the terminal.

### Steps:
1. **Accessing the Variable:**
    - Use the `echo` command to print the value of the `FLAG` variable.
    - `$FLAG` is how you access the value of the variable.
    ```bash
    echo $FLAG
    ```
  
2. **Output:**
    ```bash
    pwn.college{cdPkWi4Qr0Yr6GpC2-C87_hA11a.ddTN1QDLyMTN0czW}
    ```

### Explanation:
- `echo $FLAG` prints the value stored in the variable `FLAG`. This is the simplest way to output the content of a variable in Bash.

---

## Challenge 2: Setting Variables

Here, you will learn how to assign a value to a variable.

### Problem:
- Set a variable called `PWN` with the value `COLLEGE`.

### Steps:
1. **Assigning a Variable:**
    - In Bash, you assign variables with the syntax `VAR_NAME=value` (no spaces around `=`).
    ```bash
    PWN=COLLEGE
    ```

2. **Output:**
    ```bash
    You've set the PWN variable properly! Here's the flag:
    pwn.college{o62uadHNV7dTaxF4d4zBdBHL7hO.dlTN1QDLyMTN0czW}
    ```

### Explanation:
- `PWN=COLLEGE` assigns the string `COLLEGE` to the variable `PWN`. When you print `$PWN`, it will output `COLLEGE`.

---

## Challenge 3: Multi-word Variables

This challenge introduces the concept of **quoting** in Bash to handle multi-word values.

### Problem:
- Set the `PWN` variable to `COLLEGE YEAH` (two words).

### Steps:
1. **Assigning Multi-word Values:**
    - To handle spaces in a variable's value, you need to wrap the value in quotes.
    ```bash
    PWN="COLLEGE YEAH"
    ```

2. **Output:**
    ```bash
    You've set the PWN variable properly! Here's the flag:
    pwn.college{EOD5p8Sh3kgiRV_1rBokLQR49xE.dBjN1QDLyMTN0czW}
    ```

### Explanation:
- Quoting allows you to handle spaces in variable values. Without quotes, Bash treats spaces as argument separators, and you would get an error.
- Single (`' '`) or double (`" "`) quotes can be used, but double quotes allow variable expansion within the string.

---

## Challenge 4: Exporting Variables

In this challenge, you’ll learn how to **export variables** so they are accessible in child processes (e.g., sub-shells).

### Problem:
- Set `PWN=COLLEGE`, `COLLEGE=PWN`, and export only `PWN`.

### Steps:
1. **Assign the Variables:**
    - Set the values of `PWN` and `COLLEGE`.
    ```bash
    PWN=COLLEGE
    COLLEGE=PWN
    ```

2. **Export the Variable:**
    - Export `PWN` so it is accessible in any child processes.
    ```bash
    export PWN
    ```

3. **Run the Challenge:**
    ```bash
    /challenge/run
    ```

4. **Output:**
    ```bash
    CORRECT! You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN.
    Here's your flag:
    pwn.college{w7ZCovvUhC00AM_qbIAuLTv1Sq-.dJjN1QDLyMTN0czW}
    ```

### Explanation:
- **Exporting** a variable with `export VAR_NAME` ensures that the variable is available to any sub-process (e.g., a script or command). Variables that are not exported are only available in the current shell.
- In this case, `PWN` is accessible in the child shell, but `COLLEGE` is not.

---

## Challenge 5: Printing Exported Variables

This challenge demonstrates how to list all the exported variables in your environment.

### Problem:
- Print the value of the `FLAG` variable from the environment.

### Steps:
1. **List Environment Variables:**
    - Use the `env` command to print all exported environment variables.
    ```bash
    env
    ```

2. **Filter for `FLAG`:**
    - Use `grep` to search for the `FLAG` variable in the environment.
    ```bash
    env | grep FLAG
    ```

3. **Output:**
    ```bash
    FLAG=pwn.college{IkFRIvFxwa0NImgaEl6LN1jNLLz.dhTN1QDLyMTN0czW}
    ```

### Explanation:
- The `env` command shows all the exported environment variables, and using `grep` allows you to filter the output to find a specific variable.

---

## Challenge 6: Storing Command Output in Variables

This challenge teaches you how to capture the output of a command and store it in a variable using **command substitution**.

### Problem:
- Store the output of the command `/challenge/run` into a variable `PWN`.

### Steps:
1. **Command Substitution:**
    - Use the `$(command)` syntax to capture the output of a command and store it in a variable.
    ```bash
    PWN=$(/challenge/run)
    ```

2. **Print the Variable:**
    ```bash
    echo "$PWN"
    ```

3. **Output:**
    ```bash
    pwn.college{ExIkL4TqU9AkLsjI9_hp5oYTciQ.dVzN0UDLyMTN0czW}
    ```

### Explanation:
- **Command Substitution** allows you to run a command and assign its output to a variable. The syntax `$(command)` executes the command and captures its output for use in the script.

---

## Challenge 7: Reading Input from the User

Here, you will use the `read` command to take input from the user and store it in a variable.

### Problem:
- Read input from the user and store it in the `PWN` variable.

### Steps:
1. **Using `read` to Accept Input:**
    - Use the `read` command to prompt the user for input.
    ```bash
    read -p "Input: " PWN
    ```

2. **Input:**
    - When prompted, input `COLLEGE`.

3. **Output:**
    ```bash
    You've set the PWN variable properly! Here's the flag:
   

 pwn.college{IS_Ojbii4iw-GVaq-luyHMA-5Ck.dhzN1QDLyMTN0czW}
    ```

### Explanation:
- The `read` command takes input from the user and stores it in the specified variable. The `-p` option allows you to display a prompt.

---

## Challenge 8: Reading Files into Variables

This final challenge demonstrates how to read the contents of a file into a variable.

### Problem:
- Read the contents of the file `/challenge/run` into the `PWN` variable without using `cat`.

### Steps:
1. **Reading File Content into a Variable:**
    - Use the `read` command to read the contents of a file directly into a variable.
    ```bash
    read PWN < /challenge/run
    ```

2. **Print the Variable:**
    ```bash
    echo "$PWN"
    ```

3. **Output:**
    ```bash
    pwn.college{your_final_flag_here}
    ```

### Explanation:
- The `read` command can read the contents of a file into a variable when you redirect the file's contents using `<`. This is a cleaner alternative to using `cat` in simple cases.

---

## Conclusion

By working through these challenges, you’ve learned:
- How to set and use variables in Bash.
- How to handle multi-word strings using quoting.
- The importance of exporting variables for child processes.
- How to store command output in variables.
- Reading input from users and files efficiently.


---
