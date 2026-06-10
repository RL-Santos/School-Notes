# File Permissions
This will include a lot of topic including chmod, umask and ACLs

### Basic Permissions
- **Read (r)**, allows you to view contents of a file
- **Write (w)**, allows you to create, modify or delete a file
- **Execute (x)**, allows you to run the file as a program or directory

## Example Output
`drwxrw-r-- 2 ubuntu ubuntu-group 4096 Oct 2 11:55 files`

- **drwxrw-r--** - this is the permissions user are able to do
- **ubuntu** - this next one is the owner of the file, usually the one that created the file
- **ubuntu-group** - this is the group of people who can access the file
- **4069** - this is the size of meta data of the file but for directory this doesn't mean its the size of the files inside it just the folder metadata
- **Oct 2 11:55** - this is the time stamp on when is the content last modified
- **files** - this is the name of the directory or the file

### Permissions Breakdown
`drwxrw-r--`

- **d** - this determines if its a file or a directory
- **rwx** - this first 3 letters are the permission of the owner of the file
- **rw-** - this next 3 letters represent what the group can do
- **r--** - this last 3 letters represent what the rest of the users can do, those who are not the owner or in the group

Keep in mind that `-` means that specific group or user can't do what is should do like for example here: `rw-`, this user can read and write this file but can't execute because it has a dash on where the execute should be.

Also, if the first letter `d` is just a `-` then that means its a file not a directory or a folder.

## Numeric Permission
The permissions can be represented as a number when you will be granting or revoking permissions in a file

| Permission  | Numeric Value |
|:-----------:|:-------------:|
| Read (r)    |       4       |
| Write (w)   |       2       |
| Execute (x) |       1       |

For example you want to be able to read and write and not execute so thats `rw-`, you just add what is there value in this case thats `4 + 2` so its numerical value is 6. 

## Special Permission Bits
there are special permission that will do their own thing not just rwx

| Permission  | Commands | Display Output | Description   |
|:-----------:|:--------:|:--------------:|:-------------:|
| SUID        | `chmod <owner>+s <file>` | -rw**s**r-xr-x | No matter who runs this file, it will always think its the owner |
| SGID        | `chmod <group>+s <file or directory>` | drwxr-**s**r-x | Works like SUID but when set in a directory, all the files created inside will inherit the directory's group permission |
| Sticky Bit  | `chmod +t <directory>` | drwxrwxrw**t** | Can only be set on a directory and this only allows users to delete their own files |

To remove these permissions, you just need to replace the `+` to `-` for example, `chmod ubuntu-s files.txt`. This removes the SUID permission to files.txt

## Default Permissions and UMASK
The default permission for ***files*** is 666 and 777 for ***directories***. But this is not always the case, because we have what we call **umask** which basically overrides all default permission depending on its value.

The umask I have in my laptop is `0002` which is usually used for shared systems. Each number correspond to a specific permission. 

| Position | What it modifies    |
|:--------:|:-------------------:|
| First    | Special Permissions |
| Second   | Owner               |
| Third    | Group               |
| Fourth   | Other User          |

For example, the original default permission of a file is *666* and the umask is *0022*. Now the default permission whenever you make a file whenever you make one will be *644*. Whenever you change the umask it doesn't subtract from the default permission, it subtracts from the original which is 666 for files and 777 for directories. 


## Access Control Lists (ACLs)
this is used if you want to give a specific user a specific permission. In the table below explains what each letter does and just go to **Commands** below to elaborate more

| Entry Type | What it modifies    |
|:----------:|:-------------------:|
| u or user  | Specific user       |
| g or group | Specific group      |
| m or mask  | Maximum permission  |
| o or other | Other User          |

Example command is `setfacl -m g:user-group:rw <file name>` - this modifies the **user-group**'s permission to read and write in the file specified. But now if you remove the user it becomes `setfacl -m g::rw <file name>`, this now modifies every group that can access it not just a specific one.

## How Do Linux Evaluates Permissions?
Linux doesn't just check it all at the same time it checks it like an if-ifelse-else statement. Basically it asks,

1. **Is it the Owner?**, if yes then give owner permission
2. **Has an ACL user entry?**, if yes then give ACL user permission
3. **Is in Group?**, if yes then give group permission
4. **Has an ACL group entry?**, if yes then give ACL group permission
5. **If none of those?**, then give others permission

## Commands:
there are 3 basic commands used to determine the permission of a file and to modify them

- **chmod**, use this if you want to modify ***all*** the permission in a file
- **chown**, use this if you want to modify only the ***owner*** of the file 
- **chgrp**, use this if you want to modify only the ***group*** of the file 

### Examples:
`chmod 755 <file name>` - this command gives this permission `rwxr-xr-x`, which means owner can read, write and execute but group and others can only read and execute. This is usually used for executable files or directories  
`chmod 777 <file name>` - this now gives the highest permission to everyone `rwxrwxrwx`, this can pose as security risk on a shared systems  

--- 

`chown ubuntu <file name>` - this means you are changing the owner of the specified file to ubuntu  
`chown ubuntu:ubuntu-group <file name>` - this command now change both the owner and the group associated with it  

---

`chgrp ubuntu-group <file name>` - this means you are now changing only the group that can access the file

---

`umask 0022` - this changes the umask value to 0022

---

`setfacl -m u:user:rw <file name>` - this modifies the **user**'s permission to read and write in the file specified  
`setfacl -m g:user-group:rw <file name>` - this modifies the **user-group**'s permission to read and write in the file specified  
`setfacl -m m::rw <file name>` - this modifies the everyone that can access this file to read and write as their maximum permission. But everyone who doesn't have a read or write will not gain permission
`setfacl -m o::rw <file name>` - this modifies everyone in the **others** category to read and write in the file specified  
`setfacl -x u:user:rw <file or directory>` - this removes the **user**'s permission to read and write in the file specified. You can also use the `-x` command to remove other permission not just users  
`setfacl -R -m u:user:rw <file name>` - this modifies the **user**'s permission to read and write but now everything inside the file or directory will also change not just this file  


## Source
https://youtu.be/o_2aXxEqtao