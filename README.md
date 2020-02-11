# Jetson TX2 Container contracts Application sample with X11
This is a sample TX2 application using optional containers, which get deployed based on the L4T version that is running on each particular device.

This application installs L4T BSP archive along xfce and gstreamer in container, and starts a Desktop session at runtime.

A gstreamer pipeline test using hardware acceleration can be run from web terminal using:

```bash
$ gst-launch-1.0 videotestsrc ! 'video/x-raw, format=(string)I420,width=(int)640, height=(int)480' ! omxh264enc ! 'video/x-h264, stream-format=(string)byte-stream' ! h264parse ! omxh264dec ! nvoverlaysink -e
```

GStreamer console output will show logs from the hardware acceleration plugins:

```bash
NvMMLiteOpen : Block : BlockType = 261 
NVMEDIA: Reading vendor.tegra.display-size : status: 6 
NvMMLiteBlockCreate : Block : BlockType = 261 
Allocating new output: 640x480 (x 24), ThumbnailMode = 0
OPENMAX: HandleNewStreamFormat: 3605: Send OMX_EventPortSettingsChanged: nFrameWidth = 640, nFrameHeight = 480 
```
