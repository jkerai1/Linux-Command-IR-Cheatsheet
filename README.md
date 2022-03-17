# Linux-Command-IR-Cheatsheet

# Check Users:

cat /etc/shadow 
cat etc/passwd

# Check Open Connections:
netstat -natp (display all,address port,offload state,proto)  
netstat -la | grep “LISTEN” “ESTABLISHED”

# Check last user:

last
cat /var/log/secure* |grep ssh |grep Accept  
cat /var/log/secure* |grep ftp |grep Accept 

# Process List:

ps -elf   
ps auxf  
ls /proc/*/exe -la   


# Bash History:
cat .bash_history  
su <user> then history

# Check Cron Jobs
crontab -l 
ls -la /etc/cron.daily

# Modified Files: 
find / -mtime -o -ctime -5

# Check rootkit 
sudo chkrootkit (sudo apt install chkrootkit)

# Check common files, see what doesn't belong:
ls /tmp -lab  
ls /var/tmp -lab  
ls /dev/shm -lab    

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
  
# journalctl:  
journalctl -u networking.service  
journalctl --since "2018-10-16 13:28"  

  
  
  
https://explainshell.com
