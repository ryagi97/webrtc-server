# WebRTC Server

Ultra simple signalling server and web page designed to display a video from
a gstreamer pipeline using `webrtcsink`.

## Requirements

This project requires `webrtcsink` from [gst-plugins-rs](https://gitlab.freedesktop.org/gstreamer/gst-plugins-rs). Due to compatibility problems between gstreamer and Nvidia's deepstream, V0.9 of gst-plugins-rs is used.

## Usage

### Launch the server

```sh
docker compose build
docker compose up
```

## Setup a simple GST pipeline

```sh
gst-launch-1.0 videotestsrc ! webrtcsink meta="meta, name=myStreamName"
```



