
---

# **Linux Privilege Escalation Challenge Writeup**

This writeup covers several challenges centered around user privilege escalation in a Linux environment. You will learn how to use the `su` command to switch users, crack password hashes, and utilize `sudo` for accessing restricted files.

## **1. Becoming Root with `su`**

In this challenge, you are tasked with using the `su` command to switch to the root user. Unlike modern systems, this challenge has a root password, which you will need to provide to gain root access.

### **Steps:**

1. Use the `su` command:
   ```bash
   hacker@users~becoming-root-with-su:~$ su  
   Password: hack-the-planet
   ```

2. After successfully logging in as root, read the flag:
   ```bash
   root@users~becoming-root-with-su:/home/hacker# cat /flag  
   pwn.college{w6jaFI-dFgKkk2GYvcmKUp07-s1.dVTN0UDLyMTN0czW}
   ```

---

## **2. Other Users with `su`**

The `su` command can also be used to switch to any user account by providing the username. In this challenge, you must switch to the `zardus` user.

### **Steps:**

1. Switch to `zardus`:
   ```bash
   hacker@users~other-users-with-su:~$ su zardus  
   Password: dont-hack-me
   ```

2. Run the command to get the flag:
   ```bash
   zardus@users~other-users-with-su:/home/hacker$ /challenge/run  
   Congratulations, you have become Zardus! Here is your flag:  
   pwn.college{E4sBFPnvzlOo71ydaZVIraYPXZD.dZTN0UDLyMTN0czW}
   ```

---

## **3. Cracking Passwords**

This challenge involves cracking a password hash from the `/etc/shadow` file. You are provided with a leaked version of this file located at `/challenge/shadow-leak`.

### **Steps:**

1. Use John the Ripper to crack the password:
   ```bash
   hacker@users~cracking-passwords:~$ john /challenge/shadow-leak  
   ```

2. The output reveals that the password for `zardus` is `aardvark`:
   ```bash
   1g 0:00:00:23 100% 2/3 0.04336g/s 252.5p/s 252.5c/s 252.5C/s Johnson..buzz
   ```

3. Switch to `zardus` using the cracked password:
   ```bash
   hacker@users~cracking-passwords:~$ su zardus  
   Password: aardvark
   ```

4. Finally, run the command to get the flag:
   ```bash
   zardus@users~cracking-passwords:/home/hacker$ /challenge/run  
   Congratulations, you have become Zardus! Here is your flag:  
   pwn.college{AOa9kr6FvkqVKc-eWqfgDKV1yvi.ddTN0UDLyMTN0czW}
   ```

---

## **4. Using `sudo`**

In this challenge, you are granted `sudo` access, which allows you to execute commands as another user, including the root user.

### **Steps:**

1. Attempt to use `sudo` to read the flag:
   ```bash
   hacker@users~using-sudo:~$ sudo cat /flag  
   pwn.college{g72HINzt4CjiNaqK-HgDOf3tgkN.dhTN0UDLyMTN0czW}
   ```

---

## **Conclusion**

This series of challenges illustrates the importance of understanding user permissions and the various commands available for privilege escalation in Linux. By utilizing `su`, cracking passwords, and leveraging `sudo`, you can navigate through different levels of access and retrieve sensitive information, such as flags. 

---

