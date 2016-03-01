# Scale-AV Monitoring Computer

**Note:** This is a work in progress, designed in preparation for Scale 15x (March, 2017).


This repository holds the python, GStreamer, and GTK+ reworking of the ScaleAV video stream monitoring software. This solution has several advantages above the original solution:

- **Unified Window and Event code:**
  The same solution handels the tracking of window events, and the window display removing the need for external event tracking.
- **GStreamer:**
  GStreamer allows greater control over the incoming streams, and provides a lightweight alternative to VLC windows. This will yield better performance in the post XVideo-driver systems. GStreamer usage replaces several technologies including Jack Audio, and VLC with a single technology choice.
- **Python:** 
  A unified solution in python replaces a multi-language, multi-technology stack, which reduces the learning curve and minimizes the codebase. This allows for easier maintainability in a volunteer-staffed environment.

## Design
[[https://docs.google.com/drawings/d/173OipduHdTkx1bb0--o-LMuFIiH6ajzB7sv9MUP0DLI/pub?w=1355&h=763|alt=Design Image]]

## Installation and Execution

These instructions assume a Debian/Ubuntu system with Python 3 installed.
**Note:** Only tested on Ubuntu

**Installation:**
```
sudo apt-get install -y git gir1.2-gtk-3.0 gir1.2-gst-plugins-base-1.0 python3-gi gstreamer-1.0 python3-gst-1.0 libcanberra-gtk3-module
git clone https://github.com/LeStarch/scaleav-monitor.git
```
**Execution:**
```
cd gstreamer-pencil-tests
python3 -m app.main
```

## Known Bugs
- Windows are designed to regenerate when killed, forcing an external process termination
- If a window is killed too quickly after regneration, property-not-found errors may arise due to incomplete initialization

## Docker Support

Docker is being considered as one of the Scale-AV global deployment strategies. Thus it would be convenient to use Docker to deploy the monitoring application.

**Working Features:**
- Build from Dockerfile
- X11 support
- Video

**Known Bugs:**
- DBus support
- Audio

**Recommendation:** A simple dependency install script may be advisable to a full Docker build for this application.


