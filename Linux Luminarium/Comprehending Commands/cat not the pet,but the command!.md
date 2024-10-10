hacker@commands~cat-not-the-pet-but-the-command:~$ cd /challenge
hacker@commands~cat-not-the-pet-but-the-command:/challenge$ ls
DESCRIPTION.md  run
hacker@commands~cat-not-the-pet-but-the-command:/challenge$ cat DESCRIPTION.md 
One of the most critical Linux commands is `cat`.
`cat` is most often used for reading out files, like so:

```console
hacker@dojo:~$ cat /challenge/DESCRIPTION.md
One of the most critical Linux commands is `cat`.
`cat` is most often used for reading out files, like so:
```

`cat` will con**cat**enate (hence the name) multiple files if provided multiple arguments.
For example:

```console
hacker@dojo:~$ cat myfile
This is my file!
hacker@dojo:~$ cat yourfile
This is your file!
hacker@dojo:~$ cat myfile yourfile
This is my file!
This is your file!
hacker@dojo:~$ cat myfile yourfile myfile
This is my file!
This is your file!
This is my file!
```

Finally, if you give no arguments at all, `cat` will read from the terminal input and output it.
We'll explore that in later challenges...

In this challenge, I will copy the flag to the `flag` file in your home directory (where your shell starts).
Go read it with `cat`!
hacker@commands~cat-not-the-pet-but-the-command:/challenge$ cat flag 
cat: flag: No such file or directory
hacker@commands~cat-not-the-pet-but-the-command:/challenge$ 

## Write-Up: `cat` Command Challenge

1. **Login and Navigate:**
   After logging into the challenge environment, navigate to the appropriate directory:
   ```bash
   ls
   ```

2. **View the Flag:**
   Use the `cat` command to display the contents of the `flag` file:
   ```bash
   cat flag
   ```

3. **Flag:**
   The flag is displayed as:
   ```
   pwn.college{whw6CczFPKeaVK_HPMap2HjwG81.dFzN1QDLyMTN0czW}
   ```

### Conclusion
This challenge demonstrated the use of the `cat` command to read the contents of files, a simple yet powerful tool in Linux.