# Update & Upgrade

To update and upgrade is one of the main task for system maintenance. Like buildings without maintenance for a long time, programs without upgrading will age faster, lose functionality until they are unavailable.

Get to know the differences between the terms **Update** and **Upgrade**([Extended reading](https://support.websoft9.com/docs/faq/tech-upgrade.html#update-vs-upgrade))
- Patching operating system is **Updating**, while Ubuntu16.04 to Ubuntu18.04 means **Upgrading**.
- MySQL5.6.25 to MySQL5.6.30 means **Updating**, yet MySQL5.6 to MySQL5.7 means **Upgrading**.

Maintenance for RabbitMQ includes the following two tasks.

- Update system (Operating System and Runtime) 
- Upgrade RabbitMQ

## Update System 

### For Linux

Run a command to complete updating the Linux system:

``` shell
#For Ubuntu&Debian
apt update && apt upgrade -y

#For Centos&Redhat
yum update -y --skip-broken
```
> This deployment package is pre-configured with a scheduled task for automatic updating. If you want to remove the automatic updating, please delete the corresponding Cron.

### For Windows

The update of the Windows server is similar to that of the local computer. Manually find the update management program and set the automatic download automatic update.

## Upgrade application

Different application have different upgrade solution, you can refer to each **application administrator guide** for upgrade.



