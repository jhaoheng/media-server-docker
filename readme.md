# how to use

1. generate ssl 
  1. `cd ./nginx/ssl`
  2. `. generate-CA.sh`
2. select service
  1. media-server = ossrs
    - `docker-compose -f docker-compose-ossrs.yml up`
  2. media-server = nginx-rtmp-module
    - `docker-compose -f docker-compose-nginx-rtmp-module.yml up`
  3. try rtmpt ? ref docker-compose-xxxx.yml
    - Push streaming to localhost please use `127.0.0.1`, if not will make error of `Cannot find session for URI`

# about rtmps

> 推流工具請參考 wiki

- rtmp+tls 本身透過 nginx stream 進行 proxy_pass
- 將 docker-compose.yml 中的 `ossrs`、`proxy-rtmpt` 關閉
- 開啟 `proxy-rtmp`、`nginx-rtmp` 的服務
- 使用 `docker-compose up` 進行驗證 : `ffmpeg ... rtmps://...`，預設定 ngx_stream_ssl_module 的 ssl_verify_client=off
- 遇到多數推流失敗，都是推流的 lib 不支援或者 rtmps header 錯誤，造成 media-server 讀取失敗

## test ffmpeg for test rtmpt / rtmp

> ffmpeg push rtmps have an error 

```
ffmpeg -re -stream_loop -1 -i {path}/{name}.mp4 -vcodec libx264 -vprofile baseline -acodec aac -ar 44100 -strict -2 -ac 1 -f flv -s 1280x720 -q 10 rtmpt://127.0.0.1/demo/video
```

## 關於 ngx_rtmp_module.so
目前 compile 的版本為 debug



