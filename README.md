# Linux-Command-IR-Cheatsheet

# Check Users:

cat /etc/shadow  
cat etc/passwd

# Check Open Connections:
netstat -natp (display all,address port,offload state,proto)  
netstat -la | grep “LISTEN” “ESTABLISHED”
lsof -i -P

# Check last user:

last  
cat /var/log/secure* |grep ssh |grep Accept  
cat /var/log/secure* |grep ftp |grep Accept 

# Process List:

ps -elf   
ps auxf  
ls /proc/*/exe -la   
**you can use strings and pipe into less for proc**

# Bash History:
cat .bash_history  
su <user> then history

# Modified Files: 
find / -mtime -o -ctime -5

# Check rootkit 
sudo chkrootkit (sudo apt install chkrootkit)

# Logs: 
cd /var/log  
cat syslog | less  
cat auth.log | less   (/var/log/secure if on CentOS/Redhat. user auth logs are stored here)  
cat maillog | less  
cat boot.log | less   (bootup messages)  
cat kern | less  (/var/log/kern.log - Kernel logs)  
cat dmesg | less   
cat faillog | less  
cat cron | less  
cat httpd | less ( web server)  
cat mysqld.log | less  
cat /var/log/messages (generic messages)  
cat /var/log/faillog  - (or /btmp -failed logon attempts )  
cat /var/log/yum.log  (if yum is used to install packages)  
cat /var/log/wtmp    - login records  
cat /var/log/ufw  - firewall log  
cat /var/log/dpkg.log  - package log  
  
# Cron  
crontab -l   
ls -la /etc/cron.hourly   
ls -la /etc/cron.daily  

# Services:
service --status-all | column  
  
# Check kernel matches OS:  

uname -a   
cat/proc/version  
  
# Check common files, see what doesn't belong:
ls /tmp -lab  
ls /var/tmp -lab  
ls /dev/shm -lab    

  
# journalctl:  
journalctl -u networking.service  
journalctl --since "2018-10-16 13:28"  

  
 # Using netstat and PS together:  
  
 netstat -anp | grep ESTABLISHED | awk {'print $7}' | awk -F '/' {'print $1'} | uniq` ; do ps -eo pid,uid,ruser,etime | grep $i ; done  
  
https://explainshell.com
https://github.com/la3ar0v/TuxResponse
https://github.com/FSecureLABS/LinuxCatScale
