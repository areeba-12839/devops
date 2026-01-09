pd-tools-2.4.6   12/25 
  Verifying        : libxslt-1.1.34-12   13/25 
  Verifying        : mod_http2-2.0.26-   14/25 
  Verifying        : mod_lua-2.4.62-10   15/25 
  Verifying        : nginx-filesystem-   16/25 
  Verifying        : php-8.0.30-4.el9.   17/25 
  Verifying        : php-cli-8.0.30-4.   18/25 
  Verifying        : php-common-8.0.30   19/25 
  Verifying        : php-fpm-8.0.30-4.   20/25 
  Verifying        : php-mbstring-8.0.   21/25 
  Verifying        : php-mysqlnd-8.0.3   22/25 
  Verifying        : php-opcache-8.0.3   23/25 
  Verifying        : php-pdo-8.0.30-4.   24/25 
  Verifying        : php-xml-8.0.30-4.   25/25 

Installed:
  apr-1.7.0-12.el9.x86_64                      
  apr-util-1.6.1-23.el9.x86_64                 
  apr-util-bdb-1.6.1-23.el9.x86_64             
  apr-util-openssl-1.6.1-23.el9.x86_64         
  centos-logos-httpd-90.8-3.el9.noarch         
  httpd-2.4.62-10.el9.x86_64                   
  httpd-core-2.4.62-10.el9.x86_64              
  httpd-filesystem-2.4.62-10.el9.noarch        
  httpd-tools-2.4.62-10.el9.x86_64             
  libbrotli-1.0.9-7.el9.x86_64                 
  libxslt-1.1.34-12.el9.x86_64                 
  mailcap-2.1.49-5.el9.noarch                  
  mod_http2-2.0.26-5.el9.x86_64                
  mod_lua-2.4.62-10.el9.x86_64                 
  nginx-filesystem-2:1.20.1-26.el9.noarch      
  oniguruma-6.9.6-1.el9.6.x86_64               
  php-8.0.30-4.el9.x86_64                      
  php-cli-8.0.30-4.el9.x86_64                  
  php-common-8.0.30-4.el9.x86_64               
  php-fpm-8.0.30-4.el9.x86_64                  
  php-mbstring-8.0.30-4.el9.x86_64             
  php-mysqlnd-8.0.30-4.el9.x86_64              
  php-opcache-8.0.30-4.el9.x86_64              
  php-pdo-8.0.30-4.el9.x86_64                  
  php-xml-8.0.30-4.el9.x86_64                  

Complete!
[root@stapp03 ~]# yum install httpd php php-mysql -y
Last metadata expiration check: 0:00:13 ago on Fri Jan  9 18:03:18 2026.
Package httpd-2.4.62-10.el9.x86_64 is already installed.
Package php-8.0.30-4.el9.x86_64 is already installed.
No match for argument: php-mysql
Error: Unable to find a match: php-mysql
[root@stapp03 ~]# sed -i 's/Listen 80/Listen 8086/g' /etc/httpd/conf/httpd.conf
[root@stapp03 ~]# systemctl start httpd
[root@stapp03 ~]# systemctl enable httpd
Created symlink /etc/systemd/system/multi-user.target.wants/httpd.service → /usr/lib/systemd/system/httpd.service.
[root@stapp03 ~]# exit
# ==========================================
# SERVER 1: Database Server (stdb01)
# ==========================================
# Login: ssh peter@stdb01
# Password: Sp!dy

sudo -i

# 1. Install & Start MariaDB
yum install mariadb-server -y
systemctl start mariadb
systemctl enable mariadb

# 2. Configure Database (Run this block inside the mysql shell)
mysql -u root <<EOF
CREATE DATABASE kodekloud_db5;
CREATE USER 'kodekloud_top'@'%' IDENTIFIED BY 'YchZHRcLkL';
GRANT ALL PRIVILEGES ON kodekloud_db5.* TO 'kodekloud_top'@'%';
FLUSH PRIVILEGES;
EXIT;
EOF

exit  # Logout from root
exit  # Logout from stdb01


# ==========================================
# SERVER 2: App Host 1 (stapp01)
# ==========================================
# Login: ssh tony@stapp01
# Password: Ir0nM@n

sudo -i

# 1. Install Packages (Using php-mysqlnd)
yum install httpd php php-mysqlnd -y

# 2. Change Apache Port to 8086
sed -i 's/Listen 80/Listen 8086/g' /etc/httpd/conf/httpd.conf

# 3. Start Apache
systemctl start httpd
systemctl enable httpd

exit  # Logout from root
exit  # Logout from stapp01


# ==========================================
# SERVER 3: App Host 2 (stapp02)
# ==========================================
# Login: ssh steve@stapp02
# Password: Am3ric@

sudo -i

# 1. Install Packages
yum install httpd php php-mysqlnd -y

# 2. Change Apache Port to 8086
sed -i 's/Listen 80/Listen 8086/g' /etc/httpd/conf/httpd.conf

# 3. Start Apache
systemctl start httpd
systemctl enable httpd

exit  # Logout from root
exit  # Logout from stapp02


# ==========================================
# SERVER 4: App Host 3 (stapp03)
# ==========================================
# Login: ssh banner@stapp03
# Password: BigGr33n

sudo -i

# 1. Install Packages
yum install httpd php php-mysqlnd -y

# 2. Change Apache Port to 8086
sed -i 's/Listen 80/Listen 8086/g' /etc/httpd/conf/httpd.conf

# 3. Start Apache
systemctl start httpd
systemctl enable httpd

exit  # Logout from root
exit  # Logout from stapp03