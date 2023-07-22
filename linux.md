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

9. **softlink**: ls -s <source> <destination> 
    - in softlink if we delete source it will delete destination also (defrent inodes)
10. **hardlink**: ls <source> <destination>
    - in hardlink if we delete the source it will not delete the destination becouse both will maintain the same "inode".
11. 


