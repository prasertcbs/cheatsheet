# `FFmpeg`

# trim video
## from - to
```
ffmpeg -i video.mp4 -ss 00:01:30 -to 00:03:30 -codec copy t1.mp4
```
## from + duration
```
ffmpeg -i video.mp4 -ss 00:01:30 -t 00:03:30 -codec copy t2.mp4
```
## from hh:mm:ss - end
```
ffmpeg -i video.mp4 -ss 00:03:00 -codec copy t3.mp4
```

# concat multiple files without re-encoding
```
ffmpeg -i video.mp4 -ss 00:00:00 -to 00:03:30 -codec copy v1.mp4
ffmpeg -i video.mp4 -ss 00:04:00 -to 00:06:00 -codec copy v2.mp4
ffmpeg -i video.mp4 -ss 00:09:00 -codec copy v3.mp4
```

vlist.txt contains
```
file v1.mp4
file v2.mp4
file v3.mp4
```

```sh
ffmpeg -safe 0 -f concat -i vlist.txt -c copy output.mp4
```

# Extract the sound from a video and save it as MP3:
```sh
ffmpeg -i video.mp4 -vn audio.mp3
ffmpeg -i video.mp4 -vn audio.m4a
```
# add watermark
## create small test clip
```
ffmpeg -i video.mp4 -ss 00:01:00 -to 00:01:30 -codec copy 30sec.mp4
```
## place watermark at top right corner
```
ffmpeg -i 30sec.mp4 -i watermark.png -filter_complex "overlay=x=(main_w-overlay_w)-15:y=15" w.mp4
```
## place watermark at buttom right corner
```
ffmpeg -i 30sec.mp4 -i watermark.png -filter_complex "overlay=x=(main_w-overlay_w)-15:y=(main_h-overlay_h)-15" w.mp4
```
