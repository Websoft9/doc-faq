# 账号密码

下面分别就数据库和操作系统的账号密码进行说明：

## 数据库

### 用户名、密码和管理地址

不同的数据库有一定的差异，参考下表：

| 名称                    | 用户名     | 密码           | 可视化管理地址           |
| ----------------------- | ---------- | -------------- | ------------------------ |
| MySQL/Mariadb PHP环境中 | root       | 123456 或 存储在服务器中 | http://公网IP/phpmyadmin |
| MySQL/Mariadb 其他      | root       | 123456 或 存储在服务器中 | http://公网IP:9090       |
| PostgreSQL              | postgres   | 123456 或 存储在服务器中 | http://公网IP:9090       |
| Mongodb                 | adminmongo | 123456 或 存储在服务器中 | http://公网IP:9091       |
| Oracle                  | system     | 123456 或 存储在服务器中 | 暂无                     |
| SQLServer               | sa         | websoft9! 或 存储在服务器中 | 使用客户端管理           |

### 获取数据库密码

#### Linux系统

对于Linux系统来说，数据库密码存储在您的服务器指定文件中：*`/credentials/password.txt`*。建议通过云控制台直接连接服务器，进入命令终端，运行cat命令获取数据库密码：

![运行cat命令](https://libs.websoft9.com/Websoft9/DocsPicture/zh/common/catdbpassword-websoft9.png)

#### Windows系统

对于Windows系统来说，数据库密码存储在您的服务器指定文件中：*`c:/credentials/password.txt`*

服务器的桌面上会有打开数据库密码文件的快捷方式



## 操作系统

不同的云平台操作系统账号是不一样的，有的云平台可以在创建服务器时自定义用户名称，有的是固定用户名`root`。因此，请根据云平台查看对应的内容:[《云平台指南》](/zh/tech-instance.md)