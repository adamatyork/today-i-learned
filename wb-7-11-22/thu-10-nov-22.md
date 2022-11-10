# Thursday 10th November 2022

**Today I Learned**
<br>


You can use `FFmpeg` to query and convert video and audio files. <br>

To convert video from `.mov` to `.mp4`:
```
ffmpeg -i mymovie.mov mymovie.mp4
```

To alter the frame rate of the video:
```
ffmpeg -i mymovie.mov -r 60 mymovie60fps.mov
```

To isolate the audo stream of a video file:
```
ffmpeg -i mymovie.mov -vn audioonly.mp3
```

`ffprobe` can be used to output info on the file.

```
ffprobe mymovie.mov
```

Outputs:

```
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'mymovie.mov':
  Metadata:
    major_brand     : qt
    minor_version   : 0
    compatible_brands: qt
    creation_time   : 2022-11-10T13:56:04.000000Z
  Duration: 00:00:09.33, start: 0.000000, bitrate: 11846 kb/s
  Stream #0:0[0x1](und): Video: h264 (High) (avc1 / 0x31637661), yuv420p(tv, smpte170m/bt709/bt709, progressive), 1620x1080, 11777 kb/s, 27.12 fps, 27.08 tbr, 600 tbn (default)
    Metadata:
      creation_time   : 2022-11-10T13:56:04.000000Z
      handler_name    : Core Media Video
      vendor_id       : [0][0][0][0]
      encoder         : H.264
  Stream #0:1[0x2](und): Audio: aac (LC) (mp4a / 0x6134706D), 44100 Hz, mono, fltp, 62 kb/s (default)
    Metadata:
      creation_time   : 2022-11-10T13:56:04.000000Z
      handler_name    : Core Media Audio
      vendor_id       : [0][0][0][0]
```

You can see the framerate is **27.12 fps** <br>
The codec being used is **H.264 (AVC)** <br>
The audio stream of the file is **AAC**

<br>

## Ref. Links. Etc.

[FFmpeg Article](https://opensource.com/article/17/6/ffmpeg-convert-media-file-formats) <br>
[FFmpeg Documentation](https://ffmpeg.org/ffmpeg.html) <br>
[FFProbe Documentation](https://ffmpeg.org/ffprobe.html)
