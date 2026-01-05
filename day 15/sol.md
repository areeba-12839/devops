thor@jumphost ~$ ssh banner@stapp03
The authenticity of host 'stapp03 (172.16.238.12)' can't be established.
ED25519 key fingerprint is SHA256:huT3i9NTOTCRs9acZ3iJr4+7JpUMiGKf2dsBb6xlkmU.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'stapp03' (ED25519) to the list of known hosts.
banner@stapp03's password: 
[banner@stapp03 ~]$ sudo yum install -y nginx

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for banner: 
CentOS Stream   45 kB/s | 6.7 kB     00:00    
CentOS Stream   18 MB/s | 8.8 MB     00:00    
CentOS Stream   47 kB/s | 6.8 kB     00:00    
CentOS Stream  1.8 MB/s |  26 MB     00:14    
CentOS Stream   46 kB/s | 7.3 kB     00:00    
CentOS Stream   37 kB/s |  20 kB     00:00    
Extra Packages  96 kB/s |  18 kB     00:00    
Extra Packages 8.3 MB/s |  20 MB     00:02    
Extra Packages 5.3 kB/s | 993  B     00:00    
Extra Packages 120 kB/s |  22 kB     00:00    
Extra Packages 295 kB/s | 259 kB     00:00    
Dependencies resolved.
===============================================
 Package
        Arch   Version         Repo       Size
===============================================
Installing:
 nginx  x86_64 2:1.20.1-26.el9 appstream  36 k
Installing dependencies:
 centos-logos-httpd
        noarch 90.8-3.el9      appstream 1.5 M
 nginx-core
        x86_64 2:1.20.1-26.el9 appstream 571 k
 nginx-filesystem
        noarch 2:1.20.1-26.el9 appstream 9.3 k

Transaction Summary
===============================================
Install  4 Packages

Total download size: 2.1 M
Installed size: 4.3 M
Downloading Packages:
(1/4): nginx-1  88 kB/s |  36 kB     00:00    
(2/4): nginx-f 107 kB/s | 9.3 kB     00:00    
(3/4): nginx-c 750 kB/s | 571 kB     00:00    
(4/4): centos- 1.2 MB/s | 1.5 MB     00:01    
-----------------------------------------------
Total          1.5 MB/s | 2.1 MB     00:01     
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                       1/1 
  Running scriptlet: nginx-filesystem-2:   1/4 
  Installing       : nginx-filesystem-2:   1/4 
  Installing       : nginx-core-2:1.20.1   2/4 
  Installing       : centos-logos-httpd-   3/4 
  Installing       : nginx-2:1.20.1-26.e   4/4 
  Running scriptlet: nginx-2:1.20.1-26.e   4/4 
  Verifying        : centos-logos-httpd-   1/4 
  Verifying        : nginx-2:1.20.1-26.e   2/4 
  Verifying        : nginx-core-2:1.20.1   3/4 
  Verifying        : nginx-filesystem-2:   4/4 

Installed:
  centos-logos-httpd-90.8-3.el9.noarch         
  nginx-2:1.20.1-26.el9.x86_64                 
  nginx-core-2:1.20.1-26.el9.x86_64            
  nginx-filesystem-2:1.20.1-26.el9.noarch      

Complete!
[banner@stapp03 ~]$ sudo mkdir -p /etc/nginx/ssl && sudo mv /tmp/nautilus.crt /etc/nginx/ssl/ && sudo mv /tmp/nautilus.key /etc/nginx/ssl/ && echo "Welcome!" | sudo tee /usr/share/nginx/html/index.html
Welcome!
[banner@stapp03 ~]$ cat /etc/nginx/nginx.conf
# For more information on configuration, see:
#   * Official English Documentation: http://nginx.org/en/docs/
#   * Official Russian Documentation: http://nginx.org/ru/docs/

user nginx;
worker_processes auto;
error_log /var/log/nginx/error.log;
pid /run/nginx.pid;

# Load dynamic modules. See /usr/share/doc/nginx/README.dynamic.
include /usr/share/nginx/modules/*.conf;

events {
    worker_connections 1024;
}

http {
    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
                      '$status $body_bytes_sent "$http_referer" '
                      '"$http_user_agent" "$http_x_forwarded_for"';

    access_log  /var/log/nginx/access.log  main;

    sendfile            on;
    tcp_nopush          on;
    tcp_nodelay         on;
    keepalive_timeout   65;
    types_hash_max_size 4096;

    include             /etc/nginx/mime.types;
    default_type        application/octet-stream;

    # Load modular configuration files from the /etc/nginx/conf.d directory.
    # See http://nginx.org/en/docs/ngx_core_module.html#include
    # for more information.
    include /etc/nginx/conf.d/*.conf;

    server {
        listen       80;
        listen       [::]:80;
        server_name  _;
        root         /usr/share/nginx/html;

        # Load configuration files for the default server block.
        include /etc/nginx/default.d/*.conf;

        error_page 404 /404.html;
        location = /404.html {
        }

        error_page 500 502 503 504 /50x.html;
        location = /50x.html {
        }
    }

# Settings for a TLS enabled server.
#
#    server {
#        listen       443 ssl http2;
#        listen       [::]:443 ssl http2;
#        server_name  _;
#        root         /usr/share/nginx/html;
#
#        ssl_certificate "/etc/pki/nginx/server.crt";
#        ssl_certificate_key "/etc/pki/nginx/private/server.key";
#        ssl_session_cache shared:SSL:1m;
#        ssl_session_timeout  10m;
#        ssl_ciphers PROFILE=SYSTEM;
#        ssl_prefer_server_ciphers on;
#
#        # Load configuration files for the default server block.
#        include /etc/nginx/default.d/*.conf;
#
#        error_page 404 /404.html;
#            location = /40x.html {
#        }
#
#        error_page 500 502 503 504 /50x.html;
#            location = /50x.html {
#        }
#    }

}

[banner@stapp03 ~]$ sudo sh -c 'cat > /etc/nginx/conf.d/nautilus-ssl.conf <<EOF
server {
    listen 443 ssl;
    server_name _;
    root /usr/share/nginx/html;
    ssl_certificate /etc/nginx/ssl/nautilus.crt;
    ssl_certificate_key /etc/nginx/ssl/nautilus.key;
    ssl_session_cache shared:SSL:1m;
    ssl_session_timeout  10m;
    ssl_ciphers PROFILE=SYSTEM;
    ssl_prefer_server_ciphers on;
}
EOF' && sudo systemctl restart nginx
[banner@stapp03 ~]$ curl -Ik https://172.16.238.12/
HTTP/1.1 200 OK
Server: nginx/1.20.1
Date: Mon, 05 Jan 2026 09:21:21 GMT
Content-Type: text/html
Content-Length: 9
Last-Modified: Mon, 05 Jan 2026 09:17:19 GMT
Connection: keep-alive
ETag: "695b819f-9"
Accept-Ranges: bytes

[banner@stapp03 ~]$ curl -Ik https://172.16.238.12/
HTTP/1.1 200 OK
Server: nginx/1.20.1
Date: Mon, 05 Jan 2026 09:22:01 GMT
Content-Type: text/html
Content-Length: 9
Last-Modified: Mon, 05 Jan 2026 09:17:19 GMT
Connection: keep-alive
ETag: "695b819f-9"
Accept-Ranges: bytes

[banner@stapp03 ~]$ ^C
[banner@stapp03 ~]$ 