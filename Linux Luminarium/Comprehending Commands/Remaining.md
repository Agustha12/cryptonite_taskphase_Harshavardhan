
---

## 1. **Catting Absolute Paths**
In this challenge, we used the `cat` command to output the contents of a file using its absolute path.
```bash
cat /flag
```
This returned the flag:  
`pwn.college{IgQmI_TfNbSKjY9AML3G9zad91Z.dlTM5QDLyMTN0czW}`

## 2. **More Catting Practice**
For this challenge, the flag was hidden in `/usr/include/xen/flag`, but without using the `cd` command. We directly accessed it using `cat`:
```bash
cat /usr/include/xen/flag
```
This returned the flag:  
`pwn.college{AcjpZyj3rrwZPH8EW7VDyw2DLy1.dBjM5QDLyMTN0czW}`

## 3. **Grepping for a Needle in a Haystack**
The `grep` command helped us search for a flag inside a file. We searched for "pwn.college" within `/challenge/data.txt`:
```bash
grep pwn.college /challenge/data.txt
```
This returned the flag:  
`pwn.college{Emb9ITG8i-CZvLoyPBxac7MilqG.ddTM4QDLyMTN0czW}`

## 4. **Listing Files**
After listing the files in `/challenge`, we ran the hidden executable to get the flag:
```bash
/challenge/7108-renamed-run-3525
```
This returned the flag:  
`pwn.college{YzM-HW8SCCHR8rMAuV_DYBF-fey.dhjM4QDLyMTN0czW}`

## 5. **Touching Files**
We used the `touch` command to create two files in `/tmp`. After that, running the challenge executable provided the flag:
```bash
touch /tmp/pwn /tmp/college
/challenge/run
```
This returned the flag:  
`pwn.college{shrMGKqBP1mKebNjK1URg2oELTf.dBzM4QDLyMTN0czW}`

## 6. **Removing Files**
After deleting a specific file, the flag was revealed by checking with the challenge executable:
```bash
rm delete_me
/challenge/check
```
This returned the flag:  
`pwn.college{AbCViJXWZA1_xKFl2HDlOdG3NRY.dZTOwUDLyMTN0czW}`

## 7. **Hidden Files**
By listing hidden files with `ls -la` and `cat`ing the correct one, we retrieved the flag:
```bash
cat /.flag-323871916132340
```
This returned the flag:  
`pwn.college{U4Rg6AFhl4Eh3rdWVcj9WeNWr8x.dBTN4QDLyMTN0czW}`

## 8. **Making Directories**
We created a directory and a file within `/tmp`, and running the challenge executable granted the flag:
```bash
mkdir /tmp/pwn
touch /tmp/pwn/college
/challenge/run
```
This returned the flag:  
`pwn.college{QrmUvLzjh18VRetDEKkIvQSGc5V.dFzM4QDLyMTN0czW}`

## 9. **Finding Files**
Using the `find` command to locate the hidden flag, we `cat` the correct file to reveal the flag:
```bash
find / -name flag
cat /usr/share/racket/pkgs/math-lib/math/private/flonum/expansion/compiled/flag
```
This returned the flag:  
`pwn.college{k78RY5FylQ0eH6DKjKuDVdCDKuz.dJzM4QDLyMTN0czW}`

## 10. **Linking Files**
We created a symbolic link to the flag file, then ran the provided script to display the flag:
```bash
ln -s /flag /home/hacker/not-the-flag
/challenge/catflag
```
This returned the flag:  
`pwn.college{c4HgzOFq_zECOaxiZoA0PIpTJ2q.dlTM1UDLyMTN0czW}`

---
