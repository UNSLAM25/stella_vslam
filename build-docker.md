# How to build the docker image

1. Clone this repository with its submodules included, using ```git clone --recurse-submodules https://github.com/UNSLAM25/stella_vslam```
1. Run ```sudo docker build -t unslam -f Dockerfile.iridescence . --build-arg NUM_THREADS=`expr $(nproc) - 1` ``` to build
1. If on Ubuntu/Linux run ```xhost +local:``` to see the GUI
1. Run ```sudo docker run -it --rm --privileged -e DISPLAY=$DISPLAY -v /tmp/.X11-unix/:/tmp/.X11-unix:ro unslam``` to execute

