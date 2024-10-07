
### Challenge Overview

The task was to run the `/challenge/run` script using a relative path from the root (`/`) directory, instead of an absolute path.

### Solution

1. **Initial Attempt:**
   Running the script with an absolute path from the root directory resulted in an error:

   ```bash
   Incorrect...
   This challenge needs a relative path!
   ```

2. **Using a Relative Path:**
   I switched to using a relative path (`challenge/run`) from the root directory:

   ```bash
   hacker@paths~implicit-relative-paths-from-:/$ challenge/run
   ```

   This resulted in the correct output and flag:

   ```
   Correct!!!
   Here is your flag:
   pwn.college{kHJf_m1dEFrODBdJ8jkq1VqXx4I.dlDN1QDLyMTN0czW}
   ```

### Conclusion

The challenge emphasized the difference between absolute and relative paths. The key was to run the script using the relative path `challenge/run` from the root (`/`). The flag was:

```
pwn.college{kHJf_m1dEFrODBdJ8jkq1VqXx4I.dlDN1QDLyMTN0czW}
```

---

