
---
## Overview

This set of challenges tests and teaches the use of "globbing" in Linux, a way to match file paths using wildcard characters like `*`, `?`, and `[]`. The goal is to master the different forms of pattern matching with minimal input. Each challenge introduces a different aspect of globbing, increasing in difficulty and complexity.

---

## Challenge 1: Matching with `*`

### Objective:
Change your directory to `/challenge` using globbing, where the argument to `cd` must be at most four characters, and then run `/challenge/run` to retrieve the flag.

### Solution:
- Use `*` to match part of the directory name. The trick is to pass only the first few characters and let globbing match the rest.
  
```bash
cd /ch*
/challenge/run
```

**Flag**: `pwn.college{EZQN3zxjLi-iondXnBwzlYN78SB.dFjM4QDLyMTN0czW}`

---

## Challenge 2: Matching with `?`

### Objective:
Change your directory to `/challenge`, but this time, replace the `c` and `l` characters in `challenge` with `?` to complete the path, and run `/challenge/run`.

### Solution:
- `?` matches exactly one character. Use it to replace `c` and `l` in the path.

```bash
cd /?ha??enge
/challenge/run
```

**Flag**: `pwn.college{oh9GkA9KVJuPsqmKiongmlvZ3Cp.dJjM4QDLyMTN0czW}`

---

## Challenge 3: Matching with `[]`

### Objective:
Use a bracket-glob pattern to match the files `file_b`, `file_a`, `file_s`, and `file_h` in `/challenge/files`, then run `/challenge/run` with the correct argument.

### Solution:
- Bracket notation `[ ]` allows you to specify multiple characters to match. Use it to match the desired files.

```bash
/challenge/run file_[absh]
```

**Flag**: `pwn.college{8kSu0YwlIbDavsGOOpVU7PBANcb.dNjM4QDLyMTN0czW}`

---

## Challenge 4: Matching Paths with `[]`

### Objective:
Run `/challenge/run` with a glob pattern that matches the absolute paths of `file_b`, `file_a`, `file_s`, and `file_h` from your home directory.

### Solution:
- Combine absolute paths with the bracket-glob to match the required files from your home directory.

```bash
/challenge/run /challenge/files/file_[absh]
```

**Flag**: `pwn.college{sKRxxeXGwbOBPubbDtNkv2DqusW.dRjM4QDLyMTN0czW}`

---

## Challenge 5: Mixing Globs

### Objective:
Match the files "challenging", "educational", and "pwning" in `/challenge/files` using a short (6 characters or less) glob pattern.

### Solution:
- Use a combination of square brackets `[ ]` and a wildcard `*` to match these files.

```bash
/challenge/run [cep]*
```

**Flag**: `pwn.college{kIUzMp_ZUmElCg9Uj56Qj0miWAE.dVjM4QDLyMTN0czW}`

---

## Challenge 6: Exclusionary Globbing

### Objective:
Run `/challenge/run` with a glob pattern that matches all files in `/challenge/files` except those starting with `p`, `w`, or `n`.

### Solution:
- Use the `[^ ]` glob pattern to exclude specific characters.

```bash
/challenge/run [^pwn]*
```

**Flag**: `pwn.college{Yb4p-DLP9gmfRURIKIGaPsIJfRN.dZjM4QDLyMTN0czW}`

---
