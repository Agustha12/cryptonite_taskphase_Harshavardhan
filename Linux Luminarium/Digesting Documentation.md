
---
### Challenge 1: An Epic Filesystem Quest

1. **Objective**: 
   Navigate through the Linux filesystem to locate hidden flags based on a series of clues provided in special files. Avoid unnecessary navigation and use careful exploration to avoid traps.

2. **Process**:
   - Start by listing hidden files and directories using `ls -a`. This will reveal hidden files like `.MEMO` or `.POINTER` that contain clues to progress.
   - Open each clue using `cat`, and follow the file paths or commands suggested in the clues. These may direct you to directories such as `/usr/share/autoconf/autoscan`, `/var/cache`, or others.
   - When clues reference files that are "trapped," do not `cd` into directories. Instead, directly `cat` the files by their absolute path to avoid getting stuck or encountering permission issues.
   - The challenge will culminate in retrieving the final flag by following all clues and avoiding traps.

**Final Flag**: `pwn.college{QC-4uVAVHKrPF1vXJ7ggW8Fa85I.dljM4QDLyMTN0czW}`

---

### Challenge 2: Learning from Documentation

1. **Objective**: 
   Understand how to properly use a program by consulting its documentation and invoking it with the correct argument.

2. **Process**:
   - According to the provided documentation, the program must be executed with the `--giveflag` argument.
   - Run the command `/challenge/challenge --giveflag` as described. The program will then validate the input and output the flag.

**Final Flag**: `pwn.college{kr3cCrBBF_NRhcj5p2LUmj58Ffd.dRjM5QDLyMTN0czW}`

---

### Challenge 3: Learning Complex Usage

1. **Objective**: 
   Learn to print specific files by passing file paths as arguments to a program.

2. **Process**:
   - The documentation for this challenge explains that the program can print arbitrary files if given the correct file path via the `--printfile` argument.
   - To obtain the flag, run the command `/challenge/challenge --printfile /flag`. This will print the contents of the `/flag` file.

**Final Flag**: `pwn.college{Qcp6muRklWyUudzTx9zAvU1VpjY.dVjM5QDLyMTN0czW}`

---

### Challenge 4: Reading Manuals

1. **Objective**: 
   Find the hidden option in a program that will reveal the flag by reading its man (manual) page.

2. **Process**:
   - Use the command `man challenge` to view the manual page for the program.
   - In the `SYNOPSIS` section of the manual, it mentions an option `--wfizwk` that prints the flag if provided with the number `414`.
   - Execute the command `/challenge/challenge --wfizwk 414` to get the flag.

**Final Flag**: `pwn.college{wfiUzwPk_YEUUTca4T14SDd_nVx.dRTM4QDLyMTN0czW}`

---

### Challenge 5: Searching Manuals

1. **Objective**: 
   Learn how to search within a man page using the search functionality to find the correct argument that reveals the flag.

2. **Process**:
   - Use `man challenge` to view the manual page, and search within it using `/` to find relevant options.
   - After searching for options related to the flag, you will find that the argument `--xtvlbqf` reveals the flag.
   - Run `/challenge/challenge --xtvlbqf` to print the flag.

**Final Flag**: `pwn.college{kPK-IGU9QG9itjS_wtni5EF4mCt.dVTM4QDLyMTN0czW}`

---

### Challenge 6: Searching for Manuals

1. **Objective**: 
   Use the `--regex` option to search for a specific pattern in the man pages to find the hidden argument that gives the flag.

2. **Process**:
   - Run `man --regex challenge` to search for all manual pages related to `challenge`.
   - The correct argument found is `--gfjobb 940`. Execute `/challenge/challenge --gfjobb 940` to get the flag.

**Final Flag**: `pwn.college{gYUGfjY9oMDbTTYI_JWGUbhZcFC.dZTM4QDLyMTN0czW}`

---

### Challenge 7: Helpful Programs

1. **Objective**: 
   Use the `--help` option in a program to get a list of available arguments and determine which one will reveal the flag.

2. **Process**:
   - Use `/challenge/challenge --help` to display the help information, which will show a list of possible arguments.
   - To find the secret value needed to retrieve the flag, use `/challenge/challenge -p`, which prints the value `804`.
   - Run `/challenge/challenge -g 804` to obtain the flag.

**Final Flag**: `pwn.college{8o0KJma44pEjP77_bpA7BvOKB83.ddjM4QDLyMTN0czW}`

---

### Challenge 8: Help for Builtins

1. **Objective**: 
   Use the shell's `help` command to find information about builtins and pass the correct argument to reveal the flag.

2. **Process**:
   - The `challenge` command in this level is a shell builtin. Use the `help challenge` command to get information about the available options.
   - The `--secret` option requires a value of `Q450ifEF`. Run the command `challenge --secret Q450ifEF` to retrieve the flag.

**Final Flag**: `pwn.college{Q450ifEFrhozfTPcxxJLwRHCT_S.dRTM5QDLyMTN0czW}`

---


