

---

### 1. Redirecting Output

The first step is redirecting the output of a command into a file. This is as simple as:

```bash
echo PWN > COLLEGE
```

In this example:
- `echo PWN` sends the string "PWN" to standard output.
- `>` redirects that output into the file `COLLEGE`. If the file doesn’t exist, it’s created.

After running the command, the file `COLLEGE` will contain the word `PWN`.

---

### 2. Redirecting More Output

Here, we’re asked to redirect the output of a program (`/challenge/run`) to a file:

```bash
/challenge/run > myflag
```

This sends the output of `/challenge/run` to the file `myflag`. Note that this challenge outputs additional information to `stderr`, which still shows in the terminal unless explicitly redirected.

---

### 3. Appending Output

Appending mode (`>>`) is different from the truncating redirection (`>`). With truncating, the file is overwritten, while with appending mode, new output is added to the end of the file.

```bash
/challenge/run >> /home/hacker/the-flag
```

This writes the first part of the flag directly to the file and then appends the second half. Using `>>` ensures that the second half doesn’t overwrite the first part.

---

### 4. Redirecting Errors

In this level, we need to separately redirect the standard output and standard error of a command. This is achieved by redirecting standard error (`stderr`) using the `2>` operator.

```bash
/challenge/run > myflag 2> instructions
```

This command:
- Redirects `stdout` to `myflag`.
- Redirects `stderr` to `instructions`.

To check the results:

```bash
cat myflag
cat instructions
```

---

### 5. Redirecting Input

We can redirect the contents of a file into a command’s input using the `<` operator.

```bash
echo COLLEGE > PWN
/challenge/run < PWN
```

Here:
- We first create the file `PWN` containing the string `COLLEGE`.
- Then, we redirect that file as input to `/challenge/run`.

---

### 6. Grepping Stored Results

You can use the `grep` command to search for specific content in a file. First, redirect the output of `/challenge/run` to a file:

```bash
/challenge/run > /tmp/data.txt
```

Then, use `grep` to find the flag in that file:

```bash
grep pwn.college /tmp/data.txt
```

This command searches for lines containing "pwn.college" in the `/tmp/data.txt` file.

---

### 7. Grepping Live Output

Instead of saving the output to a file first, you can directly pipe the output to `grep`:

```bash
/challenge/run | grep pwn.college
```

The `|` operator connects the standard output of one command (`/challenge/run`) to the standard input of another (`grep`). The result is the same as the previous example but in a more streamlined manner.

---

### 8. Grepping Errors

To search through error messages, we can redirect `stderr` to `stdout` using `2>&1` and then pipe it to `grep`:

```bash
/challenge/run 2>&1 | grep pwn
```

Here, `2>&1` merges `stderr` with `stdout`, allowing `grep` to search through both.

---

### 9. Duplicating Piped Data with `tee`

The `tee` command allows you to send output to both a file and the next command in a pipeline:

```bash
/challenge/pwn | tee data | /challenge/college
```

In this command:
- The output of `/challenge/pwn` is sent to the file `data` and piped to `/challenge/college` for further processing.
- Use `cat data` to inspect what was intercepted and ensure it’s correctly passed to the next command.

---

### 10. Writing to Multiple Programs

We can use process substitution to duplicate the output of one command into multiple commands simultaneously:

```bash
/challenge/hack | tee >( /challenge/the ) > >( /challenge/planet )
```

In this example:
- The output of `/challenge/hack` is duplicated by `tee`.
- One copy is piped into `/challenge/the`, and the other into `/challenge/planet`.

---

### 11. Split Piping Stderr and Stdout

Sometimes, you need to redirect `stdout` to one program and `stderr` to another. We can achieve this using process substitution:

```bash
/challenge/hack > >( /challenge/planet ) 2> >( /challenge/the )
```

In this case:
- `stdout` is redirected to `/challenge/planet`.
- `stderr` is redirected to `/challenge/the`.

---

