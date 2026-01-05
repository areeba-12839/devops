Last login: Mon Jan  5 09:26:42 UTC 2026 on pts/0
thor@jumphost ~$ ssh loki@172.16.238.14
loki@172.16.238.14's password: 
Last login: Mon Jan  5 09:32:09 2026 from 172.16.238.3
[loki@stlb01 ~]$ sudo printf "events {\n    worker_connections 1024;\n}\n\nhttp {\n    upstream nautilus_backend {\n        server 172.16.238.10:3001;\n        server 172.16.238.11:3001;\n        server 172.16.238.12:3001;\n    }\n\n    server {\n        listen 80;\n        location / {\n            proxy_pass http://nautilus_backend;\n        }\n    }\n}\n" | sudo tee /etc/nginx/nginx.conf
[sudo] password for loki: 
Sorry, try again.
[sudo] password for loki: 
events {
    worker_connections 1024;
}

http {
    upstream nautilus_backend {
        server 172.16.238.10:3001;
        server 172.16.238.11:3001;
        server 172.16.238.12:3001;
    }

    server {
        listen 80;
        location / {
            proxy_pass http://nautilus_backend;
        }
    }
}
[loki@stlb01 ~]$ sudo nginx -t
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
[loki@stlb01 ~]$ sudo systemctl restart nginx
[loki@stlb01 ~]$ curl http://localhost
Welcome to xFusionCorp Industries![loki@stlb01 ~]$ ^C
[loki@stlb01 ~]$ 