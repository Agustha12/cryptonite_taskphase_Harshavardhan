
---

### Challenge Overview

The goal was to run the `/challenge/run` script with an appropriate argument—a path under the home directory with exactly 3 characters, as per the challenge requirements.

### Solution

1. **Running the Script:**
   Initially, running the script without any arguments prompted the following message:

   ```bash
   You must provide an argument to /challenge/run when you invoke it!
   ```

2. **Providing an Argument:**
   After several attempts, I realized that the argument had to be a path under my home directory and exactly 3 characters long.

3. **Successful Command:**
   I ran the following command with the argument `~/a`:

   ```bash
   /challenge/run ~/a
   ```

   This resulted in the correct output:

   ```
   Writing the file to /home/hacker/a!
   ... and reading it back to you:
   pwn.college{QWCCAiXAnUffgWEgCO2madnxFbf.dNzM4QDLyMTN0czW}
   ```

### Conclusion

The key was to invoke the script with a valid path under the home directory (`~/a`), ensuring that the argument was exactly 3 characters long. The flag obtained was:

```
pwn.college{QWCCAiXAnUffgWEgCO2madnxFbf.dNzM4QDLyMTN0czW}
```

--- 
