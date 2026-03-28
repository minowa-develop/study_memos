# zabbix構築方法

以下サイト参考
<https://www.zabbix.com/download?zabbix=7.0&os_distribution=alma_linux&>os_version=9&components=server_frontend_agent&db=mysql&ws=apache

```bash
#!/bin/bash

# zabbix install
rpm -Uvh https://repo.zabbix.com/zabbix/7.0/alma/9/x86_64/zabbix-release-latest-7.0.el9.noarch.rpm
dnf install zabbix-server-mysql zabbix-web-mysql zabbix-apache-conf zabbix-sql-scripts zabbix-selinux-policy zabbix-agent

# mysql install
dnf install mysql-server
systemctl enable mysqld.service --now

# scheme import
zcat /usr/share/zabbix-sql-scripts/mysql/server.sql.gz | mysql --default-character-set=utf8mb4 -uzabbix -p zabbix

# write password
vi /etc/zabbix/zabbix_server.conf

# start server
systemctl enable zabbix-server zabbix-agent httpd php-fpm --now

# open port
firewall-cmd --add-service=http --permanent
firewall-cmd --reload
```
