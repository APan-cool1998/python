# docker-compose
  1.安装
  curl -L https://github.com/docker/compose/releases/download/1.21.2/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose加执行权限
  2.执行权限
  chmod +x /usr/local/bin/docker-compose
  3.版本查看
  docker-compose version

  tips docker 错误
  ERROR: Network dtvr declared as external, but could not be found. Please create the network manually using `docker network create dtvr` and try again.

  network未创建
  docker network create dtvr dtvr为你的卷名

  进入docker内部
  docker exec -it 8ed45924a34e bash    id
  docker exec -it 13bf14c3f7d0 bash  

# docker-compose 部署 http + uwsgi
![image](https://github.com/LionsCoderPan/python/assets/88574081/2f51a8a5-4bcf-4601-a84b-10033348c668)
![image](https://github.com/LionsCoderPan/python/assets/88574081/14be30d9-4e2e-4223-aed5-d8ae2c5dace9)

  nginx
  ![image](https://github.com/LionsCoderPan/python/assets/88574081/2c59eb1d-0d1f-4595-b164-8baf5f54190d)
  ![image](https://github.com/LionsCoderPan/python/assets/88574081/517c3fb1-bf44-4535-a707-2b92aedd10e2)

  3.docker-compose
  ![image](https://github.com/LionsCoderPan/python/assets/88574081/c0fd8e0c-9c97-4cd1-a371-f7433c9f18f2)
  ![image](https://github.com/LionsCoderPan/python/assets/88574081/c7bc5de9-9512-4309-9277-a1785f446d23)

# docker-compose https+uwsgi
  worker_processes  1;

  events {
      worker_connections  1024;
  }

  http {
    include  mime.types;

    default_type  application/octet-stream;
    sendfile        on;
    keepalive_timeout  65;
    #gzip  on;
    server {
       listen 443 ssl;
       server_name dtvr.sdodt.com; #这个域名必须是你申请ssl证书的时候绑定的域名
       ssl_certificate /etc/nginx/cert/server.crt; #SSL 证书文件路径，由证书签发机构提供
       ssl_certificate_key /etc/nginx/cert/server.key; #SSL 密钥文件路径，由证书签发机构提供
       ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:ECDHE:ECDH:AES:HIGH:!NULL:!aNULL:!MD5:!ADH:!RC4; #使用此加密套件。
       ssl_protocols TLSv1 TLSv1.1 TLSv1.2; #使用该协议进行配置。
       ssl_prefer_server_ciphers on;
	   include /etc/nginx/default.d/*.conf;
       error_page  404              /404.html;
      }


      include servers/*;
      }

  ![image](https://github.com/LionsCoderPan/python/assets/88574081/83d23b7e-ddbf-4186-82e5-5d8e3704e487)
  
  docker-compose
  ![image](https://github.com/LionsCoderPan/python/assets/88574081/c6f56fdb-1925-40d5-8521-f459edaab25c)

  1.修改了代码等文件本地
  在有docker_compose.yaml 使用docker-compose restart 服务名字
  2.查看docker 日志
  docker logs -f -t --tail=500 dtcserver1 容器名字






