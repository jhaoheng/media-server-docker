# init

1. This config help nginx to use `rtmp`, `rtmpt`, `rtmpts` protocol.
2. module
    - ngx_rtmp_module.so : 負責讓 nginx 支援 rtmp 的 protocol
    - ngx_rtmpt_proxy_module.so : 負責讓 nginx 支援 rtmpt 的 protocol


# How to create `ngx_rtmpt_proxy_module.so` / `ngx_rtmp_module.so`

- dependency : 
    1. ubuntu 16.04
    2. nginx 1.13.6
- ref : `https://jhaoheng.github.io/blogpost/docker/nginx/module/nginx_add_dynamic_module/`

# how to set nginx to support module

1. refer nginx-xxx.conf 
2. cp module (already compile) to `/etc/nginx/modules/` 
3. use `nginx -t` for test
4. use `nginx -s reload` nginx.conf

# ssl

1. Use `generate-CA.sh` to generate crt & key
2. Change the name of {your_computer_hostname}.crt & {your_computer_hostname}.key to server.crt & server.key
3. check path of `ssl_certificate` and `ssl_certificate_key` in nginx.conf

# could be useful tool in Ubuntu/Debian container

```
apt-get update && \
apt-get install iputils-ping -y && \
apt-get install procps -y && \
apt-get install vim -y && \
apt-get install lsof -y && \
apt-get install curl -y && \
apt-get install git -y && \
apt-get install openssl -y && \
apt-get install wget -y
```