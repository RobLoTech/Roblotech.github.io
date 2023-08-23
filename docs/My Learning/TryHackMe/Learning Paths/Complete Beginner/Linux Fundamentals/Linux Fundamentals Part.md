
**SSH**

Secure shell - all traffic is encrypted with cryptography
- Allows to remotely manage a given device
- Sends encrypted data over network

```
ssh <host>@MACHINE_IP
```
Example:
```
ssh tryhackme@10.10.224.148
```

**Flags and Switches**

Flags/switches
- arguments provided after most linux commands

Example:

![Alt text](<../../../../assets/Pasted image 20230729191413.png>)

**Man Page**

Source of information and documentation for linux commands or applications

```
man ls
```

**Copying and Moving Files**

To copy a file, use `cp` and then the 1) name of existing file, and the 2) name of the new file
```
cp note note2
```

To move a file, use `mv` and the same format
```
mv note2 note3
```

To determine what the file type is, use `file`. 
```python
tryhackme@linux2:~$ file note
note: ASCII text
```

**Permissions**

Switching between users:
```
su <user>
```
**Common Directories**

`/etc`
Short for 'etcetera'.  Stores system files used by OS. 

`/var`
Variable data.   Stores data frequently accessed or written by services or applications running on the system. 

`/root`
Home directory for 'root' system user.

`/tmp`
Volatile, stores temporary data.  Data is cleared/wiped on system restart. 




