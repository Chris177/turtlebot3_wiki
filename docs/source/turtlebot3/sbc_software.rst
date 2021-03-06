SBC Software Setup
==================

.. NOTE:: This instruction was tested on ``Ubuntu 16.04.1`` and ``ROS Kinetic Kame`` version.

Install the Ubuntu MATE in the Raspberry Pi 3 (TurtleBot3 BURGER)
----------------------------------------------------------------

.. WARNING:: The SDcard should have its capacity more than **8 GB** for the installation of the TurtleBot3.


Download the disk image file for Raspberry Pi 3 from the following link. 

- https://ubuntu-mate.org/raspberry-pi/

When the imaging is finished, go to the next step.

Install the Ubuntu in the Intel® Joule™ (TurtleBot3 WAFFLE)
------------------------------------------------------------

Please refer to the manual installation below.

Network Configuration
---------------------

.. image:: images/software/network_configuration.png

ROS needs IP addresses to communicate between the turtlebot and the remote PC.

Type the next to find out the IP address.

.. code-block:: bash

  ifconfig

Rectangled text is the IP address of the TurtleBot.

Do the following.

.. code-block:: bash

  gedit ~/.bashrc

Change the `localhost` into the IP address shown as follows.

.. image:: images/software/network_configuration4.png

Then, source the bashrc

.. code-block:: bash

  source ~/.bashrc

.. image:: images/software/network_configuration5.png

Manual setting (Ubuntu and ROS)
-------------------------------

.. NOTE:: Skip this step when the downloaded image is being used (Manual Installation).

[Manual] Install the Ubuntu MATE for the Raspberry Pi 3 (TurtleBot3 BURGER Model)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Download the ``Ubuntu MATE 16.04.1`` version on the Raspberry Pi 3 from the link.

- https://ubuntu-mate.org/download/

.. image:: images/preparation/download_ubuntu_mate_image.png

To install Ubuntu MATE by using the image file, please refer to the link shown below.

- https://ubuntu-mate.org/raspberry-pi/

[Manual] Install TurtleBot3 dependent ROS packages for the Raspberry Pi 3
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Download the packages by typing as follows.

.. code-block:: bash

  sudo apt-get install ros-kinetic-amcl ros-kinetic-rosserial ros-kinetic-map-server ros-kinetic-move-base

[Manual] Install the Ubuntu for the Intel® Joule™ (TurtleBot3 WAFFLE Model)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Download the image ``Ubuntu 16.04`` version in the Intel® Joule™ from the link.

- https://developer.ubuntu.com/core/get-started/intel-joule#alternative-install:-ubuntu-desktop-16.04-lts

Make a bootable USB drive to install Ubuntu.

- https://software.intel.com/en-us/node/705675#ubuntu

If necessary, see the other information in the link.

- https://software.intel.com/en-us/node/700692

[Manual] Install the ROS and packages
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. image:: images/logo_ros.png
    :align: center
    :target: http://wiki.ros.org

Install the `ROS`_ by using a simple installation script file.

.. code-block:: bash

  wget https://raw.githubusercontent.com/oroca/oroca-ros-pkg/kinetic/ros_install.sh && chmod 755 ./ros_install.sh && bash ./ros_install.sh catkin_ws kinetic

or follow the typical instruction in the link.

- http://wiki.ros.org/kinetic/Installation/Ubuntu

The next step is to install the dependent packages for the TurtleBot3 control.

.. code-block:: bash

  sudo apt-get install ros-kinetic-joy ros-kinetic-teleop-twist-joy ros-kinetic-teleop-twist-keyboard ros-kinetic-laser-proc ros-kinetic-rgbd-launch ros-kinetic-depthimage-to-laserscan ros-kinetic-rosserial-arduino ros-kinetic-rosserial-python ros-kinetic-rosserial-server ros-kinetic-rosserial-client ros-kinetic-rosserial-msgs ros-kinetic-amcl ros-kinetic-map-server ros-kinetic-move-base ros-kinetic-hls-lfcd-lds-driver ros-kinetic-urdf ros-kinetic-xacro ros-kinetic-turtlebot-teleop ros-kinetic-compressed-image-transport ros-kinetic-rqt-image-view

.. code-block:: bash

  git clone https://github.com/ROBOTIS-GIT/turtlebot3.git
  cd ~/catkin_ws && catkin_make

If catkin_make is completed without any errors, the preparation for using TurtleBot3 will be finished.

[Manual] USB settings
~~~~~~~~~~~~~~~~~~~~~

The following allows the USB port to be used for the OpenCR board without root privileges.

.. code-block:: bash

  wget https://raw.githubusercontent.com/ROBOTIS-GIT/OpenCR/master/99-opencr-cdc.rules
  sudo cp ./99-opencr-cdc.rules /etc/udev/rules.d/
  sudo udevadm control --reload-rules

.. _ROS: http://wiki.ros.org
