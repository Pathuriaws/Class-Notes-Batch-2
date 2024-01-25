# Shell Scripting Notes:
- *Shell scripting is the process of writing a series of commands in a script file that can be executed by a shell, automating tasks and operations on a computer.*
- *So in the previous class we have learnt the basic commands to write the shell script.*
---
Lets understand the each command:
```
Note: The commands are usefull to interact with Linux server because the Linux does't have a GUI( Graphical user interface). The scripts which you run will just create a folders and files with in the linux server only.
```
## commands
- **Touch command**: This command is useful to create a empty files in the any of the linux based servers.
```syntax
touch <filename>
```
- **Vi editor command**: This command is linux editor which will able to create a file and open the open without the use of touch and as well as we can open and edit the existing files as well.
```
vi <filename.sh>
(The above command creates the file and opens in vi editor )
vi <existingfile.sh>
(The above cmd is used to modify the existing file contents)
```
- _VI Command Mode_:
When you open a file with **vi**, you are initially in command mode. 

  - To enter insert mode (where you can type and edit text), press i. The cursor will change to "INSERT" at the bottom, indicating that you are in insert mode.
Insert Mode:

   - In insert mode, you can type and edit text as you would in any other text editor.
   To exit insert mode and return to command mode, press Esc (Escape key).
   Save and Exit:

    - In command mode, to save changes and exit, type :wq and press Enter. This command stands for "write" (save) and "quit" (exit).
Alternatively, you can use ZZ (press Shift + z twice) to save and exit.
   - ***Just Quit (Without Saving):**
In command mode, to quit without saving changes, type :q! and press Enter. This command stands for "quit" and forces the editor to exit without saving changes.
If changes have been made and you haven't saved them, :q! will discard the changes and quit.
   - **Save Without Exiting**:
In command mode, to save changes without exiting, type :w and press Enter

 - **What is the difference between **vi** and **Touch** command ?**
 
   - The main difference between these two commands is both of them can create the files but **touch** can create only empty files in other hand **vi** can used as a editior to add the content in the files.
   - **Touch** can be used when ever you are working on some automations. here is an example.
   ```
   In realtime you are assigned a task that is every day take database backup logs and write the logs as a sperate file for each table.
   At this scenarios we might some empty files should be created before it writes the content...So in here we might need to use Touch command.

   Touch db{0001..0100}.sql 
   (The above command will create the 100 empty files.) 
     ```

- **Cat command**:This command is used to view the contents of the file. we can also use **vi** command to view contents but its hectic process to every time open editor and close the **vi** editor. 
  - So this the simple command used to view contents
  ```
  cat <filename>
  ```
- **pwd command** : **pwd** stands for present working directory. This command is useful when you want to know the linux directry path where you are in..
```
pwd 
```
- **ls -ltr command**:
  - The ls command is used in Unix-like operating systems to list the files and directories in a directory. The -ltr option is a combination of multiple options that modify the behavior of the ls command. Here's what each part of ls -ltr means:

   - l (long format): This option displays detailed information about each file and directory, including permissions, number of links, owner, group, size, modification time, and the name of the file or directory.

    - t (sort by modification time): This option sorts the listing by modification time, with the newest files or directories appearing at the bottom.

    - r (reverse order): This option reverses the order of the listing. Without the r option, the default order is from oldest to newest; with r, the order becomes from newest to oldest.
  ```
  $ ls -ltr
    total 20
    drwxr-xr-x  2 user group 4096 Jan 20 10:00 dir1
    -rw-r--r--  1 user group   25 Jan 20 11:30 file3.txt
    -rw-r--r--  1 user group   20 Jan 21 08:45 file2.txt
    -rw-r--r--  1 user group   15 Jan 22 14:12 file1.txt
  ```
- **stat command**: This command us used to show the existing permissions of the file.
```
[ec2-user@ip-172-31-39-49 ~]$ stat file1.sh
  File: file1.sh
  Size: 121             Blocks: 8          IO Block: 4096   regular file
Device: ca01h/51713d    Inode: 8618386     Links: 1
Access: (0644/-rw-r--r--)  Uid: ( 1000/ec2-user)   Gid: ( 1000/ec2-user)
Context: unconfined_u:object_r:user_home_t:s0
Access: 2024-01-24 14:53:12.157732821 +0000
Modify: 2024-01-24 14:53:12.157732821 +0000
Change: 2024-01-24 14:53:12.157732821 +0000
 Birth: 2024-01-24 14:53:12.157732821 +0000

```
- **chmod command**:

   - The chmod command in Linux is used to change the permissions (read, write, and execute) of files and directories. The basic syntax of the chmod command is:
   ```
   chmod [options] permissions file(s)
   ```
   - Here, permissions specify the new permissions you want to set, and file(s) are the files or directories for which you want to change the permissions.
   - r (read): Allows reading or viewing the contents of a file or the list of files in a directory.

   - w (write): Allows modifying or writing to a file or creating, deleting, or renaming files within a directory.

   - x (execute): Allows executing the file if it is a program or script or entering a directory.
    
    ```
    Here 7 is the magic number.
    it will be divided into 4 2 1.
    4 - stands for read
    2 - stands for write
    1 - stands for execute
    ```
   - Assign read, write, and execute permissions to the owner, and read-only permission to the group and others:
   ```
   chmod 744 file.txt
   ``` 
   - Assign full permissions to everyone: 
   ```
   chmod 777 file.txt (Note: This is less secure and should be used cautiously.)
   ```
**mkdir command**: This command is usefull for creating the directory i.e a folder.
```
mkdir <foldername>
```
**cd command**:
This command will be used to change the directory.

```
cd <foldername>
```
**cd ..** command:
This command is used to go one step back from the directory.
```
for example you are in a folder and you want to go back to previous folder at that time we can use this command.

cd documents      # Change to the "documents" directory

Now, to move back to the parent directory, you can use the cd .. command:

cd ..            # Move back to the parent directory
```

**rm -rf command**:
    
   - rm: This is the remove command.

   - -r: This option stands for "recursive." When used, it allows the removal of directories and their contents.

- -f: This option stands for "force." It suppresses the prompts for confirmation, 
```
rm -rf <filename> or <foldername>
```
**history command**:
This command will show the list of commands which you are executed earlier in the linux server.
```
[ec2-user@ip-172-31-39-49 TestFromScript]$ history
    1  ls
    2  touch file1
    3  ls
    4  ls -lrt
    5  vi file1
    6  cat file1
    7  man ls
    8  ls -lrt
    9  mv file1 file1.sh
   10  ls -lrt
   11  touch file2
   12  ls -lrt
   13  mv file2 /root/
   14  sudo mv file2 /root/
   15  ls -la
   16  ls -lrt
   17  ls -lrt /root
   18  sudo ls -lrt /root
   19  pwd
   20  ls -ltr
   21  sudo ls -ltr /root
   22  ls -ltr

```
**mv command**:
This command be used in two ways:
One way is to move the files from source to destination.
```
sudo mv file1.sh /root

(in the above example the file will move to /root folder).

mv file1.sh file2.sh

(if you are executing mv like above then it will get renamed as we are passing the src and des as the filenames)
```
commands we have executed during class.
```
! without sudo we will get the below error.

[ec2-user@ip-172-31-39-49 ~]$ mv file2 /root/
mv: cannot stat '/root/file2': Permission denied

[ec2-user@ip-172-31-39-49 ~]$ sudo mv file2 /root/

The above file2 will get moved to /root folder. we are giving sudo here because it required super user permissions to move to /root folder.

```
- **By summerise command what we have leart till now lets write a simple shell script**
```
Note: this script will just execute the commands in the linux server shell and then cretes the files and folders with in the server only.
```
Here is the script:
```
#!/bin/bash

##################################
#Author Venkatesh
#basic commands
echo "Hi i am writing my first script"
mkdir TestFromScript
cd TestFromScript
touch create{0001..0010}.dummy
ls -ltr

```
Output of this script:

```
[ec2-user@ip-172-31-39-49 ~]$ ./file1.sh
Hi i am writing my first script
total 0
-rw-r--r--. 1 ec2-user ec2-user 0 Jan 24 15:16 create0010.dummy
-rw-r--r--. 1 ec2-user ec2-user 0 Jan 24 15:16 create0009.dummy
-rw-r--r--. 1 ec2-user ec2-user 0 Jan 24 15:16 create0008.dummy
-rw-r--r--. 1 ec2-user ec2-user 0 Jan 24 15:16 create0007.dummy
-rw-r--r--. 1 ec2-user ec2-user 0 Jan 24 15:16 create0006.dummy
-rw-r--r--. 1 ec2-user ec2-user 0 Jan 24 15:16 create0005.dummy
-rw-r--r--. 1 ec2-user ec2-user 0 Jan 24 15:16 create0004.dummy
-rw-r--r--. 1 ec2-user ec2-user 0 Jan 24 15:16 create0003.dummy
-rw-r--r--. 1 ec2-user ec2-user 0 Jan 24 15:16 create0002.dummy
-rw-r--r--. 1 ec2-user ec2-user 0 Jan 24 15:16 create0001.dummy

```