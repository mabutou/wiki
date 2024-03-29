---
description: >-
  clip from
  https://www.thegeekstuff.com/2010/11/50-linux-commands/?spm=a2c4g.11186623.2.13.431059f5ndbebj
---

# 50 Most Frequently Used UNIX

![](https://static.thegeekstuff.com/wp-content/uploads/2010/11/50-linux-commands-300x176.png)This article provides practical examples for 50 most frequently used commands in Linux / UNIX.

This is not a comprehensive list by any means, but this should give you a jumpstart on some of the common Linux commands. Bookmark this article for your future reference.

## 1. tar command examples

Create a new tar archive.

```text
$ tar cvf archive_name.tar dirname/
```

Extract from an existing tar archive.

```text
$ tar xvf archive_name.tar
```

View an existing tar archive.

```text
$ tar tvf archive_name.tar
```

More tar examples: [The Ultimate Tar Command Tutorial with 10 Practical Examples](https://www.thegeekstuff.com/2010/04/unix-tar-command-examples/)

## 2. grep command examples

Search for a given string in a file \(case in-sensitive search\).

```text
$ grep -i "the" demo_file
```

Print the matched line, along with the 3 lines after it.

```text
$ grep -A 3 -i "example" demo_text
```

Search for a given string in all files recursively

```text
$ grep -r "ramesh" *
```

More grep examples: [Get a Grip on the Grep! – 15 Practical Grep Command Examples](https://www.thegeekstuff.com/2009/03/15-practical-unix-grep-command-examples/)

## 3. find command examples

Find files using file-name \( case in-sensitve find\)

```text
# find -iname "MyCProgram.c"
```

Execute commands on files found by the find command

```text
$ find -iname "MyCProgram.c" -exec md5sum {} \;
```

Find all empty files in home directory

```text
# find ~ -empty
```

More find examples: [Mommy, I found it! — 15 Practical Linux Find Command Examples](https://www.thegeekstuff.com/2009/03/15-practical-linux-find-command-examples/)

## 4. ssh command examples

Login to remote host

```text
ssh -l jsmith remotehost.example.com
```

Debug ssh client

```text
ssh -v -l jsmith remotehost.example.com
```

Display ssh client version

```text
$ ssh -V
OpenSSH_3.9p1, OpenSSL 0.9.7a Feb 19 2003
```

More ssh examples: [5 Basic Linux SSH Client Commands](https://www.thegeekstuff.com/2008/05/5-basic-linux-ssh-client-commands/)

## 5. sed command examples

When you copy a DOS file to Unix, you could find \r\n in the end of each line. This example converts the DOS file format to Unix file format using sed command.

```text
$sed 's/.$//' filename
```

Print file content in reverse order

```text
$ sed -n '1!G;h;$p' thegeekstuff.txt
```

Add line number for all non-empty-lines in a file

```text
$ sed '/./=' thegeekstuff.txt | sed 'N; s/\n/ /'
```

More sed examples: [Advanced Sed Substitution Examples](https://www.thegeekstuff.com/2009/10/unix-sed-tutorial-advanced-sed-substitution-examples/)

## 6. awk command examples

Remove duplicate lines using awk

```text
$ awk '!($0 in array) { array[$0]; print }' temp
```

Print all lines from /etc/passwd that has the same uid and gid

```text
$awk -F ':' '$3==$4' passwd.txt
```

Print only specific field from a file.

```text
$ awk '{print $2,$5;}' employee.txt
```

More awk examples: [8 Powerful Awk Built-in Variables – FS, OFS, RS, ORS, NR, NF, FILENAME, FNR](https://www.thegeekstuff.com/2010/01/8-powerful-awk-built-in-variables-fs-ofs-rs-ors-nr-nf-filename-fnr/)

## 7. vim command examples

Go to the 143rd line of file

```text
$ vim +143 filename.txt
```

Go to the first match of the specified

```text
$ vim +/search-term filename.txt
```

Open the file in read only mode.

```text
$ vim -R /etc/passwd
```

More vim examples: [How To Record and Play in Vim Editor](https://www.thegeekstuff.com/2009/01/vi-and-vim-macro-tutorial-how-to-record-and-play/)

## 8. diff command examples

Ignore white space while comparing.

```text
# diff -w name_list.txt name_list_new.txt

2c2,3
< John Doe --- > John M Doe
> Jason Bourne
```

More diff examples: [Top 4 File Difference Tools on UNIX / Linux – Diff, Colordiff, Wdiff, Vimdiff](https://www.thegeekstuff.com/2010/06/linux-file-diff-utilities/)

## 9. sort command examples

Sort a file in ascending order

```text
$ sort names.txt
```

Sort a file in descending order

```text
$ sort -r names.txt
```

Sort passwd file by 3rd field.

```text
$ sort -t: -k 3n /etc/passwd | more
```

## 10. export command examples

To view oracle related environment variables.

```text
$ export | grep ORACLE
declare -x ORACLE_BASE="/u01/app/oracle"
declare -x ORACLE_HOME="/u01/app/oracle/product/10.2.0"
declare -x ORACLE_SID="med"
declare -x ORACLE_TERM="xterm"
```

To export an environment variable:

```text
$ export ORACLE_HOME=/u01/app/oracle/product/10.2.0
```

## 11. xargs command examples

Copy all images to external hard-drive

```text
# ls *.jpg | xargs -n1 -i cp {} /external-hard-drive/directory
```

Search all jpg images in the system and archive it.

```text
# find / -name *.jpg -type f -print | xargs tar -cvzf images.tar.gz
```

Download all the URLs mentioned in the url-list.txt file

```text
# cat url-list.txt | xargs wget –c
```

## 12. ls command examples

Display filesize in human readable format \(e.g. KB, MB etc.,\)

```text
$ ls -lh
-rw-r----- 1 ramesh team-dev 8.9M Jun 12 15:27 arch-linux.txt.gz
```

Order Files Based on Last Modified Time \(In Reverse Order\) Using ls -ltr

```text
$ ls -ltr
```

Visual Classification of Files With Special Characters Using ls -F

```text
$ ls -F
```

More ls examples: [Unix LS Command: 15 Practical Examples](https://www.thegeekstuff.com/2009/07/linux-ls-command-examples/)

## 13. pwd command

pwd is Print working directory. What else can be said about the good old pwd who has been printing the current directory name for ages.

## 14. cd command examples

Use “cd -” to toggle between the last two directories

Use “shopt -s cdspell” to automatically correct mistyped directory names on cd

More cd examples: [6 Awesome Linux cd command Hacks](https://www.thegeekstuff.com/2008/10/6-awesome-linux-cd-command-hacks-productivity-tip3-for-geeks/)

## 15. gzip command examples

To create a \*.gz compressed file:

```text
$ gzip test.txt
```

To uncompress a \*.gz file:

```text
$ gzip -d test.txt.gz
```

Display compression ratio of the compressed file using gzip -l

```text
$ gzip -l *.gz
         compressed        uncompressed  ratio uncompressed_name
              23709               97975  75.8% asp-patch-rpms.txt
```

## 16. bzip2 command examples

To create a \*.bz2 compressed file:

```text
$ bzip2 test.txt
```

To uncompress a \*.bz2 file:

```text
bzip2 -d test.txt.bz2
```

More bzip2 examples: [BZ is Eazy! bzip2, bzgrep, bzcmp, bzdiff, bzcat, bzless, bzmore examples](https://www.thegeekstuff.com/2010/10/bzcommand-examples/)

## 17. unzip command examples

To extract a \*.zip compressed file:

```text
$ unzip test.zip
```

View the contents of \*.zip file \(Without unzipping it\):

```text
$ unzip -l jasper.zip
Archive:  jasper.zip
  Length     Date   Time    Name
 --------    ----   ----    ----
    40995  11-30-98 23:50   META-INF/MANIFEST.MF
    32169  08-25-98 21:07   classes_
    15964  08-25-98 21:07   classes_names
    10542  08-25-98 21:07   classes_ncomp
```

## 18. shutdown command examples

Shutdown the system and turn the power off immediately.

```text
# shutdown -h now
```

Shutdown the system after 10 minutes.

```text
# shutdown -h +10
```

Reboot the system using shutdown command.

```text
# shutdown -r now
```

Force the filesystem check during reboot.

```text
# shutdown -Fr now
```

## 19. ftp command examples

Both ftp and secure ftp \(sftp\) has similar commands. To connect to a remote server and download multiple files, do the following.

```text
$ ftp IP/hostname
ftp> mget *.html
```

To view the file names located on the remote server before downloading, mls ftp command as shown below.

```text
ftp> mls *.html -
/ftptest/features.html
/ftptest/index.html
/ftptest/othertools.html
/ftptest/samplereport.html
/ftptest/usage.html
```

More ftp examples: [FTP and SFTP Beginners Guide with 10 Examples](https://www.thegeekstuff.com/2010/06/ftp-sftp-tutorial/)

## 20. crontab command examples

View crontab entry for a specific user

```text
# crontab -u john -l
```

Schedule a cron job every 10 minutes.

```text
*/10 * * * * /home/ramesh/check-disk-space
```

More crontab examples: [Linux Crontab: 15 Awesome Cron Job Examples](https://www.thegeekstuff.com/2009/06/15-practical-crontab-examples/)

## 21. service command examples

Service command is used to run the system V init scripts. i.e Instead of calling the scripts located in the /etc/init.d/ directory with their full path, you can use the service command.

Check the status of a service:

```text
# service ssh status
```

Check the status of all the services.

```text
service --status-all
```

Restart a service.

```text
# service ssh restart
```

## 22. ps command examples

ps command is used to display information about the processes that are running in the system.

While there are lot of arguments that could be passed to a ps command, following are some of the common ones.

To view current running processes.

```text
$ ps -ef | more
```

To view current running processes in a tree structure. H option stands for process hierarchy.

```text
$ ps -efH | more
```

## 23. free command examples

This command is used to display the free, used, swap memory available in the system.

Typical free command output. The output is displayed in bytes.

```text
$ free
             total       used       free     shared    buffers     cached
Mem:       3566408    1580220    1986188          0     203988     902960
-/+ buffers/cache:     473272    3093136
Swap:      4000176          0    4000176
```

If you want to quickly check how many GB of RAM your system has use the -g option. -b option displays in bytes, -k in kilo bytes, -m in mega bytes.

```text
$ free -g
             total       used       free     shared    buffers     cached
Mem:             3          1          1          0          0          0
-/+ buffers/cache:          0          2
Swap:            3          0          3
```

If you want to see a total memory \( including the swap\), use the -t switch, which will display a total line as shown below.

```text
ramesh@ramesh-laptop:~$ free -t
             total       used       free     shared    buffers     cached
Mem:       3566408    1592148    1974260          0     204260     912556
-/+ buffers/cache:     475332    3091076
Swap:      4000176          0    4000176
Total:     7566584    1592148    5974436
```

## 24. top command examples

top command displays the top processes in the system \( by default sorted by cpu usage \). To sort top output by any column, Press O \(upper-case O\) , which will display all the possible columns that you can sort by as shown below.

```text
Current Sort Field:  P  for window 1:Def
Select sort field via field letter, type any other key to return

  a: PID        = Process Id              v: nDRT       = Dirty Pages count
  d: UID        = User Id                 y: WCHAN      = Sleeping in Function
  e: USER       = User Name               z: Flags      = Task Flags
  ........
```

To displays only the processes that belong to a particular user use -u option. The following will show only the top processes that belongs to oracle user.

```text
$ top -u oracle
```

More top examples: [Can You Top This? 15 Practical Linux Top Command Examples](https://www.thegeekstuff.com/2010/01/15-practical-unix-linux-top-command-examples/)

## 25. df command examples

Displays the file system disk space usage. By default df -k displays output in bytes.

```text
$ df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             29530400   3233104  24797232  12% /
/dev/sda2            120367992  50171596  64082060  44% /home
```

df -h displays output in human readable form. i.e size will be displayed in GB’s.

```text
ramesh@ramesh-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              29G  3.1G   24G  12% /
/dev/sda2             115G   48G   62G  44% /home
```

Use -T option to display what type of file system.

```text
ramesh@ramesh-laptop:~$ df -T
Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/sda1     ext4    29530400   3233120  24797216  12% /
/dev/sda2     ext4   120367992  50171596  64082060  44% /home
```

## 26. kill command examples

Use kill command to terminate a process. First get the process id using ps -ef command, then use kill -9 to kill the running Linux process as shown below. You can also use killall, pkill, xkill to terminate a unix process.

```text
$ ps -ef | grep vim
ramesh    7243  7222  9 22:43 pts/2    00:00:00 vim

$ kill -9 7243
```

More kill examples: [4 Ways to Kill a Process – kill, killall, pkill, xkill](https://www.thegeekstuff.com/2009/12/4-ways-to-kill-a-process-kill-killall-pkill-xkill/)

## 27. rm command examples

Get confirmation before removing the file.

```text
$ rm -i filename.txt
```

It is very useful while giving shell metacharacters in the file name argument.

Print the filename and get confirmation before removing the file.

```text
$ rm -i file*
```

Following example recursively removes all files and directories under the example directory. This also removes the example directory itself.

```text
$ rm -r example
```

## 28. cp command examples

Copy file1 to file2 preserving the mode, ownership and timestamp.

```text
$ cp -p file1 file2
```

Copy file1 to file2. if file2 exists prompt for confirmation before overwritting it.

```text
$ cp -i file1 file2
```

## 29. mv command examples

Rename file1 to file2. if file2 exists prompt for confirmation before overwritting it.

```text
$ mv -i file1 file2
```

Note: mv -f is just the opposite, which will overwrite file2 without prompting.

mv -v will print what is happening during file rename, which is useful while specifying shell metacharacters in the file name argument.

```text
$ mv -v file1 file2
```

## 30. cat command examples

You can view multiple files at the same time. Following example prints the content of file1 followed by file2 to stdout.

```text
$ cat file1 file2
```

While displaying the file, following cat -n command will prepend the line number to each line of the output.

```text
$ cat -n /etc/logrotate.conf
    1	/var/log/btmp {
    2	    missingok
    3	    monthly
    4	    create 0660 root utmp
    5	    rotate 1
    6	}
```

## 31. mount command examples

To mount a file system, you should first create a directory and mount it as shown below.

```text
# mkdir /u01

# mount /dev/sdb1 /u01
```

You can also add this to the fstab for automatic mounting. i.e Anytime system is restarted, the filesystem will be mounted.

```text
/dev/sdb1 /u01 ext2 defaults 0 2
```

## 32. chmod command examples

chmod command is used to change the permissions for a file or directory.

Give full access to user and group \(i.e read, write and execute \) on a specific file.

```text
$ chmod ug+rwx file.txt
```

Revoke all access for the group \(i.e read, write and execute \) on a specific file.

```text
$ chmod g-rwx file.txt
```

Apply the file permissions recursively to all the files in the sub-directories.

```text
$ chmod -R ug+rwx file.txt
```

More chmod examples: [7 Chmod Command Examples for Beginners](https://www.thegeekstuff.com/2010/06/chmod-command-examples/)

## 33. chown command examples

chown command is used to change the owner and group of a file. \

To change owner to oracle and group to db on a file. i.e Change both owner and group at the same time.

```text
$ chown oracle:dba dbora.sh
```

Use -R to change the ownership recursively.

```text
$ chown -R oracle:dba /home/oracle
```

## 34. passwd command examples

Change your password from command line using passwd. This will prompt for the old password followed by the new password.

```text
$ passwd
```

Super user can use passwd command to reset others password. This will not prompt for current password of the user.

```text
# passwd USERNAME
```

Remove password for a specific user. Root user can disable password for a specific user. Once the password is disabled, the user can login without entering the password.

```text
# passwd -d USERNAME
```

## 35. mkdir command examples

Following example creates a directory called temp under your home directory.

```text
$ mkdir ~/temp
```

Create nested directories using one mkdir command. If any of these directories exist already, it will not display any error. If any of these directories doesn’t exist, it will create them.

```text
$ mkdir -p dir1/dir2/dir3/dir4/
```

## 36. ifconfig command examples

Use ifconfig command to view or configure a network interface on the Linux system.

View all the interfaces along with status.

```text
$ ifconfig -a
```

Start or stop a specific interface using up and down command as shown below.

```text
$ ifconfig eth0 up

$ ifconfig eth0 down
```

More ifconfig examples: [Ifconfig: 7 Examples To Configure Network Interface](https://www.thegeekstuff.com/2009/03/ifconfig-7-examples-to-configure-network-interface/)

## 37. uname command examples

Uname command displays important information about the system such as — Kernel name, Host name, Kernel release number,  
 Processor type, etc.,

Sample uname output from a Ubuntu laptop is shown below.

```text
$ uname -a
Linux john-laptop 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 i686 GNU/Linux
```

## 38. whereis command examples

When you want to find out where a specific Unix command exists \(for example, where does ls command exists?\), you can execute the following command.

```text
$ whereis ls
ls: /bin/ls /usr/share/man/man1/ls.1.gz /usr/share/man/man1p/ls.1p.gz
```

When you want to search an executable from a path other than the whereis default path, you can use -B option and give path as argument to it. This searches for the executable lsmk in the /tmp directory, and displays it, if it is available.

```text
$ whereis -u -B /tmp -f lsmk
lsmk: /tmp/lsmk
```

## 39. whatis command examples

Whatis command displays a single line description about a command.

```text
$ whatis ls
ls		(1)  - list directory contents

$ whatis ifconfig
ifconfig (8)         - configure a network interface
```

## 40. locate command examples

Using locate command you can quickly search for the location of a specific file \(or group of files\). Locate command uses the database created by updatedb.

The example below shows all files in the system that contains the word crontab in it.

```text
$ locate crontab
/etc/anacrontab
/etc/crontab
/usr/bin/crontab
/usr/share/doc/cron/examples/crontab2english.pl.gz
/usr/share/man/man1/crontab.1.gz
/usr/share/man/man5/anacrontab.5.gz
/usr/share/man/man5/crontab.5.gz
/usr/share/vim/vim72/syntax/crontab.vim
```

## 41. man command examples

Display the man page of a specific command.

```text
$ man crontab
```

When a man page for a command is located under more than one section, you can view the man page for that command from a specific section as shown below.

```text
$ man SECTION-NUMBER commandname
```

Following 8 sections are available in the man page.

1. General commands
2. System calls
3. C library functions
4. Special files \(usually devices, those found in /dev\) and drivers
5. File formats and conventions
6. Games and screensavers
7. Miscellaneous
8. System administration commands and daemons

For example, when you do whatis crontab, you’ll notice that crontab has two man pages \(section 1 and section 5\). To view section 5 of crontab man page, do the following.

```text
$ whatis crontab
crontab (1)          - maintain crontab files for individual users (V3)
crontab (5)          - tables for driving cron

$ man 5 crontab
```

## 42. tail command examples

Print the last 10 lines of a file by default.

```text
$ tail filename.txt
```

Print N number of lines from the file named filename.txt

```text
$ tail -n N filename.txt
```

View the content of the file in real time using tail -f. This is useful to view the log files, that keeps growing. The command can be terminated using CTRL-C.

```text
$ tail -f log-file
```

More tail examples: [3 Methods To View tail -f output of Multiple Log Files in One Terminal](https://www.thegeekstuff.com/2009/09/multitail-to-view-tail-f-output-of-multiple-log-files-in-one-terminal/)

## 43. less command examples

less is very efficient while viewing huge log files, as it doesn’t need to load the full file while opening.

```text
$ less huge-log-file.log
```

One you open a file using less command, following two keys are very helpful.

```text
CTRL+F – forward one window
CTRL+B – backward one window
```

More less examples: [Unix Less Command: 10 Tips for Effective Navigation](https://www.thegeekstuff.com/2010/02/unix-less-command-10-tips-for-effective-navigation/)

## 44. su command examples

Switch to a different user account using su command. Super user can switch to any other user without entering their password.

```text
$ su - USERNAME
```

Execute a single command from a different account name. In the following example, john can execute the ls command as raj username. Once the command is executed, it will come back to john’s account.

```text
[john@dev-server]$ su - raj -c 'ls'

[john@dev-server]$
```

Login to a specified user account, and execute the specified shell instead of the default shell.

```text
$ su -s 'SHELLNAME' USERNAME
```

## 45. mysql command examples

mysql is probably the most widely used open source database on Linux. Even if you don’t run a mysql database on your server, you might end-up using the mysql command \( client \) to connect to a mysql database running on the remote server.

To connect to a remote mysql database. This will prompt for a password.

```text
$ mysql -u root -p -h 192.168.1.2
```

To connect to a local mysql database.

```text
$ mysql -u root -p
```

If you want to specify the mysql root password in the command line itself, enter it immediately after -p \(without any space\).

## 46. yum command examples

To install apache using yum.

```text
$ yum install httpd
```

To upgrade apache using yum.

```text
$ yum update httpd
```

To uninstall/remove apache using yum.

```text
$ yum remove httpd
```

## 47. rpm command examples

To install apache using rpm.

```text
# rpm -ivh httpd-2.2.3-22.0.1.el5.i386.rpm
```

To upgrade apache using rpm.

```text
# rpm -uvh httpd-2.2.3-22.0.1.el5.i386.rpm
```

To uninstall/remove apache using rpm.

```text
# rpm -ev httpd
```

More rpm examples: [RPM Command: 15 Examples to Install, Uninstall, Upgrade, Query RPM Packages](https://www.thegeekstuff.com/2010/07/rpm-command-examples/)

## 48. ping command examples

Ping a remote host by sending only 5 packets.

```text
$ ping -c 5 gmail.com
```

More ping examples: [Ping Tutorial: 15 Effective Ping Command Examples](https://www.thegeekstuff.com/2009/11/ping-tutorial-13-effective-ping-command-examples/)

## 49. date command examples

Set the system date:

```text
# date -s "01/31/2010 23:59:53"
```

Once you’ve changed the system date, you should syncronize the hardware clock with the system date as shown below.

```text
# hwclock –systohc

# hwclock --systohc –utc
```

## 50. wget command examples

The quick and effective method to download software, music, video from internet is using wget command.

```text
$ wget http://prdownloads.sourceforge.net/sourceforge/nagios/nagios-3.2.1.tar.gz
```

Download and store it with a different name.

```text
$ wget -O taglist.zip http://www.vim.org/scripts/download_script.php?src_id=7701
```

More wget examples: [The Ultimate Wget Download Guide With 15 Awesome Examples](https://www.thegeekstuff.com/2009/09/the-ultimate-wget-download-guide-with-15-awesome-examples/)

Did I miss any frequently used Linux commands? Leave a comment and let me know.

