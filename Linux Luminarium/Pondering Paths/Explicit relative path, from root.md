
---

### Challenge Overview

This challenge required executing the `/challenge/run` script using a relative path from the root directory.

### Solution

1. **Error on Absolute Path:**
   Initially, running the script from a different directory with an absolute path resulted in:

   ```bash
   Incorrect...
   You are not currently in the / directory.
   ```

2. **Navigating to the Correct Directory:**
   I navigated to the root (`/`) directory:

   ```bash
   cd /
   ```

3. **Executing with a Relative Path:**
   After changing to the correct directory, I executed the script using a relative path:

   ```bash
   ./challenge/run
   ```

   This resulted in the correct output:

   ```
   Correct!!!
   ./challenge/run is a relative path, invoked from the right directory!
   Here is your flag:
   pwn.college{UTSUmAQcpQHJYjIsrppZMmtDSij.dBTN1QDLyMTN0czW}
   ```

### Conclusion

The challenge emphasized using an explicit relative path (`./challenge/run`) from the root directory. The flag obtained was:

```
pwn.college{UTSUmAQcpQHJYjIsrppZMmtDSij.dBTN1QDLyMTN0czW}
```

---
