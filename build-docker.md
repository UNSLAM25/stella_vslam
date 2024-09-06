# How to build and run the docker image

## Common instructions

1. Clone this repository with its submodules included, using ```git clone --recurse-submodules https://github.com/UNSLAM25/stella_vslam```
1. Go into `vlsam-backend/vlsam` folder. Copy your camera config file there. Name it `config.yaml`. Without this you won't be able to run the system.
1. Go back to the root folder of the repository.

## Linux / Ubuntu

1. Run ```sudo docker build -t unslam -f Dockerfile.iridescence . --build-arg NUM_THREADS=`expr $(nproc) - 1` ``` to build
1. Run ```xhost +local:``` to be able to see the GUI
1. Run ```sudo docker run -it --rm --privileged -e DISPLAY=$DISPLAY -v /tmp/.X11-unix/:/tmp/.X11-unix:ro unslam``` to execute

## Windows 

### Install VcXsrv 

1. Download VcXsrv from its SourceForge repository: https://sourceforge.net/projects/vcxsrv/
1. Install VcXsrv with default options.
1. Run Xlaunch which gets installed by VcXsrv, and perform the intial configuration as follows:
    1. Display setting: select the “multiple windows” option, and click “Next”.
    1. Client startup: check the “Start no client” option, and click “Next”.
    1. Extra setting: In addition to the default options, **make sure “Disable access control” is enabled, and click “Next”.**
    1. Click “Finish”.

### Building and running the image

1.  ```docker build -t unslam -f Dockerfile.iridescence . --build-arg NUM_THREADS=`<YOUR_NUMBER_OF_THREADS>` ```
1. Find your computer IP address using ```ipconfig```
1. Run the following command, replacing the values where needed: ```docker run -it --rm --privileged -p 8000:8000 -p 8765:8765 -e DISPLAY=<YOUR_IP_ADDRESS>:0.0 -v /c/Users/<YOUR_WINDOWS_USER>:/tmp/.X11-unix:ro unslam``` 


## Running UNSLAM

Once the container is up and running, type into the terminal the following command: ```python3 completeSystem.py```

You'll be able to access the web interface by navigating into localhost:8000 in Chrome.
