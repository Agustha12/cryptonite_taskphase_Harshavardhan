
### Intro to Commands

1. **Login to the Host:**
   Use SSH to connect to the challenge environment:
   ```bash
   ssh -i ./key hacker@dojo.pwn.college
   ```

2. **Run the Command:**
   Execute the `hello` command to get the flag:
   ```bash
   hello
   ```

3. **Flag:**
   ```
   pwn.college{kY6XBDkHuI8f66GJ0PjsKZMn5J7.ddjNyUDL4ITO0czW}
   ```

### Intro to Arguments

1. **Login to the Host:**
   As with the first part, login using SSH:
   ```bash
   ssh -i ./key hacker@dojo.pwn.college
   ```

2. **Command with Arguments:**
   Use the `hello` command with an argument ("hackers") in place of `echo`:
   ```bash
   hello hackers
   ```

3. **Flag:**
   The flag is revealed upon running the command:
   ```
   pwn.college{kY6XBDkHuI8f66GJ0PjsKZMn5J7.ddjNyUDL4ITO0czW}
   ```
