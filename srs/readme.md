# 關於 ossrs hook

## on_hls
```
{
  "action": "on_hls",
  "client_id": 1985,
  "ip": "192.168.1.10", "vhost": "video.test.com", "app": "live",
  "stream": "livestream",
  "duration": 9.36, // in seconds
  "cwd": "/usr/local/srs",
  "file": "./objs/nginx/html/live/livestream/2015-04-23/01/476584165.ts",
  "url": "live/livestream/2015-04-23/01/476584165.ts",
  "m3u8": "./objs/nginx/html/live/livestream/live.m3u8",
  "m3u8_url": "live/livestream/live.m3u8",
  "seq_no": 100
}
```

- 這邊的 timestamp，紀錄的是影片開始的時間
- client_id : 本次紀錄的用戶 id
- seq_no : 此 app/stream 的 ipcam streaming，總共產生的 ts 序號