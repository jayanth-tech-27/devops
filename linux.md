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

  # Perform System Maintenance in linux
  ------------------------------------

1. **Clear Temporary Files**
* Remove unnecessary temporary files from the system to free up disk space. Use the `tmpreaper` utility or manually delete files from common temporary directories like /tmp.
2. **8Update the System**: sudo apt update
3. **Check Disk Space**: `df -h`
4. **Remove Unused Packages** `sudo apt autoremove`
5. **Check System Logs**:
* Review system log files to identify any potential issues or errors. Logs are usually stored in the `/var/log` directory. Common log files include `/var/log/syslog`, `/var/log/messages`, and `/var/log/dmesg`
6. **Manage Users and Permissions**
 * Regularly review user accounts and their permissions. Remove any unnecessary or unused accounts, and ensure that users have appropriate access rights.
7. **security-updates** Stay up-to-date with security patches and updates for installed software. Security vulnerabilities can be exploited by attackers, so keeping the system updated is crucial.
8. **Reboot if Necessary**:
* Some updates may require a system reboot to take effect. If the kernel or critical system components were updated, it's essential to reboot the system to apply the changes.
9. **Backup Important Data**:
Regularly back up critical data to ensure that it's safe in case of hardware failure, accidental deletion, or other unexpected events.
10. **Check for Hardware Issues**:
Perform hardware diagnostics if you suspect any hardware problems. Use appropriate tools like memtest for memory testing.
11. **Performance Tuning (Optional)**:
Depending on your system's needs, you may perform performance tuning to optimize resource usage for specific tasks.




# backup in linux
------------------
* sudo apt-get update
* sudo apt-get install rsync
* **sudo rsync -av --delete SOURCE DESTINATION**
* The `-a` option stands for "archive mode" and is used to preserve permissions, ownership, timestamps, etc.
* The `-v` option enables verbose mode to see the progress of the backup.
* The `--delete` option ensures that files deleted from the source are also deleted from the backup destination, keeping them in sync.
* Schedule regular backups (optional): For automated backups, you can create a cron job to run the rsync command at specific intervals. Edit the crontab using: `crontab -e`
* **0 0 * * * sudo rsync -av --delete / /mnt/backup** then save the file.

# Monitor System Performance
-------------------------------
1. **netstat and ss**: These tools can help you monitor network connections and statistics. For example, you can use `netstat -tuln` or `ss -tuln` to list all listening TCP and UDP connections.
2. **Free command**: The free command displays information about system memory usage, including total, used, and available memory. Simply run free in the terminal.

3. **htop**: Besides being a process viewer, `htop` also shows real-time CPU and memory usage.
4. **top** - is a basic process monitoring tool available by default on most Linux distributions.
5. **vmstat**: vmstat reports virtual memory statistics, including memory, swap, and CPU usage. Run it with vmstat followed by the interval in seconds (e.g., vmstat 5).
