NGINX RTMP Dockerfile
=====================

This Dockerfile installs NGINX configured with `nginx-rtmp-module`, ffmpeg
and some default settings for HLS live streaming.

**Note: in the current state, this is just an experimental project to play with
RTMP and HLS.**


How to user
-----------

1. Build and run the container (`docker build -t nginx_rtmp .` &
   `docker run -p 1935:1935 -p 8080:80 --rm nginx_rtmp`).

2. Stream your live content to `rtmp://localhost:1935/encoder/stream_name` where
   `stream_name` is the name of your stream.

3. In Safari, VLC or any HLS compatible browser / player, open
   `http://localhost:8080/hls/stream_name.m3u8`. Note that the first time,
   it might take a few (10-15) seconds before the stream works. This is because
   when you start streaming to the server, it needs to generate the first
   segments and the related playlists.

Change Log
----------

20160328
--------

Added feature to serve static files in /usr/share/nginx/html

```
docker run -p 1935:1935 -p 8080:80 -v /path/to/html:/usr/share/nginx/html:ro --rm nginx_rtmp:root_index
open http://localhost:8080/
```

Links
-----

* http://nginx.org/
* https://github.com/arut/nginx-rtmp-module
* https://www.ffmpeg.org/
* https://obsproject.com/
