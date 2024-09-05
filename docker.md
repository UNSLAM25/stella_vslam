# How to build the docker image

1. Clone this repository with its submodules included
1. Run ```sudo docker build -t unslam -f Dockerfile.iridescence . --build-arg NUM_THREADS=`expr $(nproc) - 1` ``` to build
1. Run ```sudo docker run -it --rm --privileged -e DISPLAY=$DISPLAY -v /tmp/.X11-unix/:/tmp/.X11-unix:ro unslam``` to execute