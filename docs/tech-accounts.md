# Username and Password

## Database and application

**For Linux Server**, use the **SSH** to connect your Server and run the command `sudo cat /credentials/password.txt` to get the username and password of this deployment solution.

![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/common/catdbpassword-websoft9.png)

**For Windows Server**, you can find the *Shortcuts icon* for the path *`c:/credentials/password.txt`*


**Database reference for you:**

| Database name      | username     | password           | Web based GUI    |
| ----------------------- | ---------- | -------------- | ------------------------ |
| MySQL/Mariadb      | root       | stored in your Server | http://Cloud Server Internet IP:9090       |
| PostgreSQL              | postgres   | stored in your Server | http://Cloud Server Internet IP:9090       |
| Mongodb                 | root | stored in your Server | http://Cloud Server Internet IP:9091       |
| Oracle                  | system     | stored in your Server |                      |
| SQLServer               | sa         | stored in your Server |            |


## Operating System

Different cloud platform operating system accounts are different. Some cloud platforms can customize the user name when creating a server, and some have a fixed user name of `root`. Therefore, please check the corresponding content according to the cloud platform: ["Cloud Platform Guide"](/tech-instance.md)