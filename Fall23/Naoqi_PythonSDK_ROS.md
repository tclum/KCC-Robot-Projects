# NAO Options?

There are two different ways to program on the NAO without Choregraphe
  1. On the commandline using python directly (this can be done in Mac & Windows without the VPN)
  2. On the commandline using ROS (requires Ubuntu Linux 20.04) or ROS2?

## Using Python SDK
  ### First time install:
  - You must use Python 2.7
      - Ubuntu 20.04 comes with it pre-installed, not sure about the other OSs
      - **To start it, in the terminal enter: `python2`**
         - If you don't use the `2` python 3 will start
     - If Python2 is not installed, follow the instructions here: https://ubuntuforums.org/showthread.php?t=2486174
   
-   Download the Aldebaran python 2.7 SDK from: https://www.aldebaran.com/fr/support/nao-6/downloads-softwares
-   Follow the installation instructions here: http://doc.aldebaran.com/2-8/dev/python/install_guide.html
    - Summary of SDK installation
      - Save the download somewhere like in you home directory. Somewhere easy to find/remember the path.
      - Unzip the file.
      - Then you have to add the location of that to the PYTHONPATH settings in your computer so python can find it.
      - This is OS specific, follow the instructions on the website.
        - **NOTE where it says things like this ` /path/to/python-sdk/lib/python2.7/site-packages` the `/path/to/python-sdk` part has to be replaced with wherever you have unzipped the downloaded SDK.**
          - For example: on my Linux laptop I unzipped the downloaded file in a folder in my home directory which I had made called `Software/pynaoqi`.
          - When it unzips, it makes a folder called `pynaoqi2.7-2.8.6.23-linux64-20191127_152327`
          - So my `/path/to/python-sdk` is `/home/lizajane999/Software/pynaoqi/pynaoqi2.7-2.8.6.23-linux64-20191127_152327`
          - **Note** you can copy/paste the commands line-by-line from the Aldebaran site and just adjust the path, but for Mac and Linux take off the `$` at the front of each!
      - Start python2 by entering `python2` in the terminal. You should get a `>>>` prompt.
      - Enter: `import naoqi`
      - If no errors appear it is working!
      - If there are errors, then your PYTHONPATH is not right.

  ### Working with PythonSDK
  * At least this is how it works on the Dell
  * In the terminal, start python2 by entering `python2`
      - Python is an interpreted language so you can just type commands at the `>>>` prompt when it is running. (You can also run programs from files, but
      that comes later...)
    - Follow the tutorials starting here: http://doc.aldebaran.com/2-8/dev/python/intro_python.html
    - and here: http://doc.aldebaran.com/2-8/dev/python/tutorials.html#python-tutorials
    - and here: http://doc.aldebaran.com/2-8/dev/python/examples.html


   ## Using ROS
   ROS has been difficult to install!!

   - You must have Ubuntu 20.04 installed
   - Follow all of the instructions here https://wiki.ros.org/noetic/Installation/Ubuntu and do the Desktop-Full install (Do not attempt item 3. the one line installation)
   - If you successfully get the `rosdep update` done go on to the ROS tutorials https://wiki.ros.org/ROS/Tutorials
      - You don't have to do all of them, but you need to at least get roscore running and make a catkin workspace (tutorials show how)
  - THEN try to install the NAO stuff for ROS.
   - HERE IS WHERE I HAVE RUN INTO PROBLEMS!!
   - These are the instructions: https://wiki.ros.org/nao/Tutorials/Installation/remote
   - BUT!! When I try to run `catkin_make` the compiling fails because of the python Boost library. Apparently there is a library required by one of the NAO packages that is no longer in the Python2.7 Boost.
     -   I have attempted to just fudge it and erased the requirement from the CMAKE file, but it is not working.....

## BUT WAIT : ROS2 may be the answer!
- Aldebaran appears to have ROS2 drivers under active development here: https://github.com/ros-naoqi/naoqi_driver2
- I have not tried to install ROS2 or the NAO stuff but it is currently showing daily activity on GitHub
