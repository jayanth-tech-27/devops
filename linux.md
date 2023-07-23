### 1.chandge the defuilt user id in linux?
* `vi/etc/login.defs`  in that we can set the  UID_MIN  and UID_MAX based on our reqirement.
### 2. in root rm -rf /tmp/test gives an error operation not permited .Reason ?
*  chattr +i /tmp/test is excuted that why
* for remove chattr `chattr -i /tmp/test`
### 3. /etc/hosts (which RPM is responsible for creating this file) ?
* `rpm -qf /tmp/test`  this command shows that.
### 4 hard link:
* `ln targetpath destination path`
* it will maintain the data when the main file deleted also.
* **reson**: is created in same file system (same i node is maintained)
### 5. softlink
* `ln -s targetpath destination path`
* it will not maintain the data when the main file deleted.
 ### 6.what is sticky bit ?
*  it will applied for `folder only`
* wherever its implimented that folder deletion was possible only for `root user and owner of the file` 
## 7. for checking open ports on the server
* **netstat -tunlp**
* with out login **nmap-A server ip** (ensure nmap is installed)
### 8. how will you create space on disk if is is showing 100% used?
* df -h ---> show the disk usege
* df -th ---> its shows filesystems also
* du -sh *  ---> is shows the utilization we can find out what are the unusefull stuff and then deleted. if in case all memory was usefull then add a disk space to the disk

9. ### softlink: 
* `ls -s <source> <destination>` 
    - in softlink if we delete source it will delete destination also (defrent inodes)
10. ### hardlink:
*  `ls <source> <destination>`
    - in hardlink if we delete the source it will not delete the destination becouse both will maintain the same "inode".
11. ### give single command permission
    `which cp` this command give the path of that coammand and that command we shouild give in the sudors file like `chandu ALL(ALL):NOPASSWD ALL <PATH OF THT COMMAND>

12. ### change the word in perticular file
 * sed -i 's/old-text/new-text/g' input.txt
 * s: This indicates the substitution command in sed.
 *old-text: This is the text you want to find and replace.
 * new-text: This is the new text you want to replace the old text with.
 * g: This is a flag that stands for "global" and tells sed to replace all
 13. ### delete the file with particular permission.
  * `find . -type f -perm 600 -exec rm {} \;`
  * **find**: The command to search for files and directories.
  * **.**: The starting directory for the search. In this case, it is the current directory.
  * **-type f**: This option specifies that we are only interested in regular files (not directories or special files).
  * **-perm 600**: This option filters files based on their permissions. The value 600 represents read and write permissions for the owner. Note that file permissions are represented in octal notation.
  * **-exec**: This option allows us to execute a command on each file found.
  * **rm {} \;**: This part of the command is the rm command being executed for each file found. The {} will be replaced with the file names found by find, and \; is used to terminate the -exec option.