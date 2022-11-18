# Thursday 17th November 2022

**Today I Learned**
<br>

You can setup an RTSP video livestream using `docker` and `ffmpeg`. <br>
We are going to... <br>

1. Setup an RTSP server
2. Serve the stream from the server
3. Consume the stream from a client

<br>

First, we need to setup the server using docker. <br>
`aler9/simple-rtsp-server` is a docker image, publically available on DockerHub. <br>
It provides an RTSP server that can be configured to use RTSP, RTMP or HLS with either TCP or UDP. <br> <br>
DockerHub lists the full features but the most important ones are: 
- Publish live streams to the server
- Read live streams from the server
- Each stream can have multiple video and audio tracks, encoded with any codec

<br>

## Run the Server 
Let's run the docker image and tell the server to use TCP for RTSP streams. <br>

`docker run --rm -it -e RTSP_PROTOCOLS=tcp -p 8554:8554 -p 1935:1935 -p 8888:8888 aler9/rtsp-simple-server`

We map ports 8554 and 1935 on the container to ports 8554 and 1935 on our mac, so that we can communicate with the server from outside the container. <br>
8554 is used to publish and read RTSP streams, while 1935 is reserved for RTMP. <br>


___

<br>


## Serve the Stream
Let's serve up an RTSP stream to the server. <br>

`ffmpeg -re -stream_loop -1 -i myvideo.mov -f rtsp -rtsp_transport tcp rtsp://localhost:8554/mystream`

FFmpeg lets us create an infinite loop of video with `-stream_loop`. <br>
We specify RTSP using TCP with `rtsp -rtsp-transport tcp` <br>
And we give the URL we want to publish the stream to as `localhost:8554/mystream`. <br>
Note 8554 was the mapped port from earlier, reserved for RTSP. <br>
This is the URL we will use later to consume the stream.

---
<br>

## Consume the Stream
Let's see if we can consume the stream from the browser. <br>
If we navigate to `rtsp://localhost:8554/mystream` we should be prompted to open either VLC or Quicktime. <br>
We should see our video playing! <br>

We can also open the stream directly in VLC player with `vlc rtsp://localhost:8554/mystream`

<br>


## Ref. Links. Etc.
[aler9/simple-rtsp-server DockerHub](https://hub.docker.com/r/aler9/rtsp-simple-server) <br>
[aler9/simple-rtsp-server GitHub](https://github.com/aler9/rtsp-simple-server) <br>
[FFmpeg Docs -stream_loop](https://ffmpeg.org/ffmpeg.html#Main-options) <br>
