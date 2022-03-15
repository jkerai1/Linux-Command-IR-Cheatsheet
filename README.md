# Linux-Command-IR-Cheatsheet
Cheatsheet of commands for triaging a Linux system

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

ps -elf OR ps auxf
ls /proc/*/exe -la 


# Bash History
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
cd /var/log, cat syslog | less
cat auth.log | less
cat maillog | less
cat boot.log | less
cat kern | less
cat dmesg | less
cat faillog | less
cat cron | less
cat httpd | less (server)
cat mysqld.log | less

# Check kernel matches OS:

uname -a
cat/proc/version
