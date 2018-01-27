 A curated list of linux commands.
 
System Commands
^^^^^^^^^^^^^^^
- ``uname –a`` display linux system information 
- ``uname –r`` display kernel release information 
- ``uptime`` show how long system running + load 
- ``hostname`` show system host name 
- ``hostname -i`` display the IP address of the host 
- ``last reboot`` show system reboot history 
- ``date`` show the current date and time 
- ``cal`` show this month calendar 
- ``w`` display who is online
- ``whoami`` who you are logged in as 
- ``finger user`` display information about user

Hardware related

   $ dmesg - detected hardware and boot messages 
   $ cat /proc/cpuinfo - CPU model 
   $ cat /proc/meminfo - hardware memory 
   $ cat /proc/interrupts - lists the number of interrupts per CPU per I/O device 
   $ lshw - displays information on hardware configuration of the system 
   $ lsblk - displays block device related information in Linux 
   $ free -m - used and free memory (-m for MB)
   $ lspci -tv - show PCI devices 
   $ lsusb -tv - show USB devices 
   $ lshal - show a list of all devices with their properties 
   $ dmidecode - show hardware info from the BIOS
   $ hdparm -i /dev/sda -show info about disk sda 
   $ hdparm -tT /dev/sda - do a read speed test on disk sda 
   $ badblocks -s /dev/sda - test for unreadable blocks on disk sda

Statistics and Analyze

   $ top - display and update the top cpu processes
   $ mpstat 1 - display processors related statistics 
   $ vmstat 2 - display virtual memory statistics 
   $ iostat 2 - display I/O statistics (2sec Intervals)
   $ tail -n 500 /var/log/syslog - last 10 kernel/syslog messages
   $ tcpdump -i eth1 - capture all packets flows on interface eth1 
   $ tcpdump -i eth0 'port 80' - monitor all traffic on port 80 ( HTTP ) 
   $ lsof - list all open files belonging to all active processes
   $ lsof -u testuser - list files opened by specific user 
   $ free –m - show amount of RAM 
   $ watch df –h - watch changeable data continuously

Users

   $ id - show the active user id with login and group
   $ last - show last logins on the system 
   $ who - show who is logged on the system
   $ groupadd admin - add group "admin" (force add existing group) 
   $ useradd -c "Joe Smith" -g admin -m joe - Create user "joe" and add to group "admin"
   $ userdel joe - delete user joe (force,file removal) 
   $ adduser joe - add user "joe" 
   $ usermod - modify user information

File Commands

   $ ls –al - display all information about files / directories
   $ ls -alR - display all information about files / directories recursively
   $ pwd - show current directory path
   $ mkdir directory-name - create a directory
   $ rm file-name - delete file
   $ rm -r directory-name - delete directory recursively 
   $ rm -f file-name - forcefully remove file 
   $ rm -rf directory-name - forcefully remove directory recursively 
   $ cp file1 file2 - copy file1 to file2 
   $ cp -r dir1 dir2 - copy dir1 to dir2, create dir2 if it doesn’t exist 
   $ mv file1 file2 - move files from one place to another
   $ ln –s /path/to/file-name link-name - create symbolic link to file-name
   $ touch file - create or update file 
   $ cat > file - place standard input into file
   $ more file - output the contents of file 
   $ head file - output the first 10 lines of file
   $ tail file - output the last 10 lines of file
   $ tail -f file - output the contents of file as it grows starting with the last 10 lines 
   $ gpg -c file - encrypt file
   $ gpg file.gpg - decrypt file

Process Related

   $ ps - display your currently active processes
   $ ps aux | grep 'telnet' - find all process id related to telnet process 
   $ pmap - memory map of process 
   $ top - display all running processes 
   $ kill pid - kill process with mentioned pid id
   $ killall proc - kill all processes named proc 
   $ pkill processname - send signal to a process with its name 
   $ bg - resumes suspended jobs without bringing them to foreground 
   $ fg - brings the most recent job to foreground 
   $ fg n - brings job n to the foreground

File Permission Related

   $ chmod octal file-name - change the permissions of file to octal , which can be found separately for user, group and world; octal value 4 -read 2 –write 1 –execute
   $ chown owner-user file - change owner of the file 
   $ chown owner-user:owner-group file-name - change owner and group owner of the file 
   $ chown owner-user:owner-group directory - change owner and group owner of the directory

Network

   $ ifconfig –a - display all network ports and ip address
   $ ifconfig eth1 mtu 9000 up - set mtu to 9000
   $ ifconfig eth0 - display specific ethernet port ip address and details 
   $ ifconfig -a | grep HWaddr - display MAC address

   change MAC address:
   # ifconfig eth0 down
   # ifconfig eth0 hw ether 00:80:48:BA:d1:30
   # ifconfig eth0 up

   $ ip addr show - display all network interfaces and ip address (available in iproute2 package,powerful than ifconfig) 
   $ ip address add 192.168.0.1 dev eth0 - set ip address 
   $ ethtool eth0 - linux tool to show ethernet status (set full duplex , pause parameter) 
   $ mii-tool eth0 - linux tool to show ethernet status (more or like ethtool) 
   $ ping host - send echo request to test connection (learn sing enhanced ping tool)
   $ whois domain - get who is information for domain 
   $ dig domain - get DNS information for domain (screenshots with other available parameters) 
   $ dig -x host - reverse lookup host 
   $ host google.com - lookup DNS ip address for the name
   $ hostname –i - lookup local ip address (set hostname too) 
   $ wget file - download file (very useful other option) 
   $ netstat -tupl - listing all active listening ports(tcp,udp,pid) 

   WiFi related:
   $ iwconfig wlan0 essid "mynetworkESSID" - specify ESSID for the WLAN
   $ dhclient wlan0 - to receive an IP address, netmask, DNS server and default gateway from the Access Point
   $ iwconfig wlan0 mode managed key [WEP key] - 128 bit WEP use 26 hex characters, 64 bit WEP uses 10
   $ iwconfig wlan0 mode master - set the card to act as an access point mode
   $ iwconfig wlan0 mode managed - set card to client mode on a network with an access point
   $ iwconfig wlan0 mode ad-hoc - set card to peer to peer networking or no access point mode
   $ iwconfig wlan0 mode monitor - set card to RFMON mode
   $ iwconfig wlan0 essid any - with some cards you may  disable the ESSID checking
   $ iwconfig wlan0 key 1111-1111-1111-1111 - set 128 bit WEP key
   $ iwconfig wlan0 key off - disable WEP key
   $ iwconfig wlan0 key open - sets open mode, no authentication is used and card may accept non-encrypted sessions
   $ iwlist wlan0 scan - give the list of Access Points and Ad-Hoc cells in range (ESSID, Quality, Frequency, Mode etc.)
   $ iwlist wlan0 power - list the various Power Management attributes and modes of the device
   $ iwlist wlan0 txpower - list the various Transmit Power available on the device
   $ iwlist wlan0 retry - list the transmit retry limits and retry lifetime on the device

Compression / Archives

   $ tar cf test.tar test - create tar named test.tar containing test/ 
   $ tar xf test.tar - extract the files from test.tar 
   $ tar czf test.tar.gz test - create a tar with gzip compression 
   $ gzip test - compress file and renames it to test.gz

Install Package

   $ rpm -i pkgname.rpm - install rpm based package
   $ rpm -e pkgname - remove package 

   Install from source 
   $ ./configure 
   $ make 
   $ make install

   $ apt-get update - re-synchronize the package index files from their sources
   $ apt-get upgrade - install the newest versions of all packages currently installed on the system from the sources
   $ apt-get install package - install package
   $ apt-get remove package - remove package
   $ apt-cache search package - search for package

Search

   $ grep pattern files - search for pattern in files 
   $ grep -r pattern dir - search recursively for pattern in dir 
   $ locate file - find all instances of file 
   $ find /home/tom -name 'index*' - find files names that start with "index"
   $ find /home -size +10000k - find files larger than 10000k in /home

Login (ssh and telnet)

   $ ssh user@host - connect to host as user 
   $ ssh -p port user@host - connect to host using specific port 
   $ telnet host - connect to the system using telnet port

File transfer

   scp
   $ scp file.txt server2:/tmp  - secure copy file.txt to remote host /tmp folder
   $ scp gordon@server2:/www/*.html /www/tmp - copy *.html files from remote host to current system /www/tmp folder 
   $ scp -r gordon@server2:/www /www/tmp - copy all files and folders recursively from remote server to the current system /www/tmp folder 

   rsync 
   $ rsync -a /home/apps /backup/ - synchronize source to destination 
   $ rsync -avz /home/apps gordon@192.168.10.1:/backup - synchronize files/directories between the local and remote system with compression enabled

Disk Usage

   $ df –h - show free space on mounted filesystems
   $ df -i - show free inodes on mounted filesystems 
   $ fdisk -l - show disks partitions sizes and types 
   $ du -ah - display disk usage in human readable form
   $ findmnt - displays target mount point for all filesystem
   $ mount device-path mount-point - mount a device

Directory

   $ cd .. - go up one level of the directory tree
   $ cd - go to $HOME directory 
   $ cd /test - change to /test directory

Keyboard shortcuts

   Alt+Ctrl+T - open Terminal Window

   Alt+Ctrl+L - lock the screen
   Alt+Ctrl+Del - logoff

   Alt+F4 - close current window
   Alt+F2 - pop up command window (for quickly running commands)

   Super-W  - show all windows in the current workspace
   Ctrl+Super+D - show desktop

   Ctrl+A - select all items on list or text
   Ctrl+C - copy all selected items to clipboard
   Ctrl+X - cut all selected items to clipboard
   Ctrl+V or Mouse middle button click - paste all selected items to clipboard

   PrintScr - takes screenshot
   Alt+PrintScr - takes screenshot of windows
   Shift+PrintScr - takes screenshot of selected window area
