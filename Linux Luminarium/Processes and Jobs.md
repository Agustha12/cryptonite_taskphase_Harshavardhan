

```markdown
# Process Manipulation Walkthrough

This guide provides explanations and examples of common process manipulation commands and how they were used to complete a series of challenges.

## 1. Listing Processes

### Command: `ps`

The `ps` command is used to list currently running processes in the system. It provides details such as the process ID (PID), the user running the process, CPU usage, and the command that started the process.

- `ps -ef`: Displays a detailed list of running processes with information about the user, parent process, and more.
- `ps aux`: Provides additional columns for CPU and memory usage, making it useful for identifying resource-heavy processes.

In the first challenge, the `/challenge/run` script has been renamed, and the `/challenge` directory cannot be listed directly. We use `ps` to find the running renamed script. By checking the process list, we find something like `/challenge/8759-run-19024` and execute that to retrieve the flag.

```bash
ps -ef
/challenge/8759-run-19024
```

### Flag
```
pwn.college{IQ-2BkncywkKNdTFVu-W8_8enfB.dhzM4QDLyMTN0czW}
```

---

## 2. Killing Processes

### Command: `kill`

To terminate or kill a process, we first need to identify it using the `ps` command, and then use the `kill` command with the process ID (PID). This stops the process from running.

In this challenge, we need to kill a process named `/challenge/dont_run`. To do this:
1. Use `ps -ef` or `ps aux` to locate the process and its PID.
2. Use `kill <PID>` to terminate the process.

```bash
ps -ef | grep /challenge/dont_run
kill <PID>
```

### Flag
```
pwn.college{gVd7mIdfAe38R7y4xLwM2ubUZOD.dJDN4QDLyMTN0czW}
```

---

## 3. Interrupting Processes

### Method: `Ctrl-C`

To manually interrupt a running process, we can use the keyboard shortcut `Ctrl-C`. This sends a signal to the process to stop immediately.

In this challenge, we are asked to interrupt the execution of a process. Run the process and press `Ctrl-C` to stop it, which returns the flag.

```bash
/challenge/run
# Press Ctrl-C to stop the process
```

### Flag
```
pwn.college{gg8M_KEmOPc2--pyMlONzLEKfrm.dNDN4QDLyMTN0czW}
```

---

## 4. Suspending Processes

### Method: `Ctrl-Z`

To temporarily stop (suspend) a running process, use the `Ctrl-Z` command. This sends the process to the background in a "suspended" state. You can later resume it.

In this challenge, run the process and suspend it using `Ctrl-Z`. Once it is suspended, run another copy of the same process.

```bash
/challenge/run
# Press Ctrl-Z to suspend the process
/challenge/run
```

### Flag
```
pwn.college{41PGAkxklWPepJZysY6qFWB12tO.dVDN4QDLyMTN0czW}
```

---

## 5. Resuming Processes

### Command: `fg`

When a process is suspended using `Ctrl-Z`, you can bring it back to the foreground using the `fg` command. This resumes the process, allowing it to continue running as if it was never stopped.

In this challenge:
1. Suspend the process using `Ctrl-Z`.
2. Use the `fg` command to bring the process back to the foreground and complete it.

```bash
/challenge/run
# Press Ctrl-Z to suspend the process
fg
```

### Flag
```
pwn.college{UfaHFlL4zqAKxPoec9koSVXz7SS.dZDN4QDLyMTN0czW}
```

---

## 6. Backgrounding Processes

### Command: `bg`

To resume a suspended process in the background, use the `bg` command. This allows you to continue working on other tasks while the process runs in the background.

1. First, suspend the process with `Ctrl-Z`.
2. Then, resume it in the background with `bg`.

```bash
/challenge/run
# Press Ctrl-Z to suspend the process
bg
```

### Flag
```
pwn.college{0SsKoqMz4ggS8f1-tVhoSeOO9ZF.ddDN4QDLyMTN0czW}
```

---

## 7. Foregrounding Processes

### Command: `fg`

If a process is running in the background and you need to bring it to the foreground, you can use the `fg` command.

1. First, start the process and suspend it with `Ctrl-Z`.
2. Resume it in the background using `bg`.
3. Finally, bring it to the foreground using `fg`.

```bash
/challenge/run
# Press Ctrl-Z to suspend the process
bg
fg
```

### Flag
```
pwn.college{MsXVWAmgS4VhsrUHLA2qa-hBsY-.dhDN4QDLyMTN0czW}
```

---

## 8. Starting Background Processes

### Method: `&`

To start a process in the background immediately, you can append an `&` to the command. This will run the process in the background and return the terminal prompt, allowing you to execute other commands while the process runs.

```bash
/challenge/run &
```

### Flag
```
pwn.college{Ak7fYbT0cQgc_utvLLmUnSNYVLx.dlDN4QDLyMTN0czW}
```

---

## 9. Process Exit Codes

### Command: `$?`

Every process in Linux returns an exit code when it completes. An exit code of `0` means the process was successful, while any other number indicates an error or different outcome. The special variable `$?` stores the exit code of the last executed command.

In this challenge:
1. Run the process to get the exit code.
2. Use `echo $?` to display the exit code.
3. Submit the exit code to complete the challenge.

```bash
/challenge/get-code
echo $?
/challenge/submit-code <exit_code>
```

### Flag
```
pwn.college{4cqStLswWjRvLhxs-NxIEddowxJ.dVDN4QDLyMTN0czW}
```

---

## Conclusion

This guide covers the most common process manipulation commands in Linux. By using commands such as `ps`, `kill`, `fg`, `bg`, and others, you can manage processes effectively and complete a variety of challenges.