# Useful commands

These commands may be useful for you to manege application on Linux:

## System

```
# Reboot Linux system
reboot 

# View memory usage
free

# View disk usage
df -hl 

# View Docker containers usage
sudo docker ps -a

```

## File management

```
# Down load the file from URL
wget url  

# Uzip xx.zip to current directory
unzip xx.zip

# Go to target directory
cd /data/wwwroot

# Modify the owner and group for target directory
chown -R nginx.nginx /data/wwwroot

# Modify the read,write,execute permission for target directory
find /data/wwwroot/default -type f -exec chmod 640 {} \;
find /data/wwwroot/default -type d -exec chmod 750 {} \;
```

## Service management

```
# Restart Nginx
systemctl restart nginx

# Restart php-fpm
systemctl restart php-fpm 

# Restart Apache HTTP
systemctl restart apache

# Upgrade all software on System, not upgrade System core
yum upgrade -y

# Upgrade System core and all software on System
yum update -y
```