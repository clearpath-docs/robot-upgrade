Upgrading Your Robot OS
========================

Once you have backed up your ROS Melodic robot's important files on a separate computer, you can install Ubuntu 20.04 with ROS Noetic onto your robot's computer. 

Ubuntu provides a command-line tool for doing an in-place upgrade called ``do-release-upgrade``, but we do not recommend upgrading this way: doing an in-place upgrade can leave stale configuration files. We find it is better to do a fresh install and then restore the backed-up data you made in the previous step.

.. note::

    If your robot uses an Nvidia Jetson as its main PC, skip down to the "Upgrading Jetson" section at the bottom of this page

Download the ISO
-----------------

Clearpath Robotics has customized OS installation images for all of our robots available online:
http://packages.clearpathrobotics.com/stable/images/latest/noetic-focal/amd64/

Open the link and download the latest ISO for Ubuntu 20.04 and ROS Noetic.

Write ISO to USB Drive
-----------------------

After the ISO has finished downloading, insert a USB drive of at least 2GB into your computer and use a tool like ``unetbootin`` (on Linux) or ``rufus`` (on Windows) to write the ISO to the USB drive. This will erase all data already on the drive, so make sure you've backed up anything important!

.. image:: images/unetbootin.png
  :alt: Unetbootin

Install the OS
---------------

.. note::

    The following is a general overview of how to reinstall your robot's OS. Specific robots may require additional steps, such as removing cover plates to access USB/ethernet/HDMI/VGA ports, etc.... Please refer to your robot's manual for specific information on how to reinstall the OS on that model of robot.

.. warning::

    While it is highly unlikely, it is possible that the robot's wheels could turn while the OS is installing. We recommend placing the robot on blocks and/or engaging the e-stop during the OS installation.

Make sure your robot is powered off and either has freshly-charged batteries installed or is connected to shore power. Connect a keyboard and monitor to the robot, and make sure it has internet access by connecting an ethernet cable between the robot's computer and an internet source (e.g. router).

Insert the USB drive you set up in the previous step into a USB port on the robot and power the robot on. Depending on your robot's computer, you will need to press F1, F2, F7, F12, or DELETE while the robot is booting to open the boot menu and select the USB drive to boot from.

After your choose to boot the computer from the USB drive, the computer will restart. The installer should then run automatically. Step through any prompts that come up. Make sure you select the installation option corresponding to your robot, and give your robot an appropriate hostname; presumably the same hostname as before. The robot will power off automatically when the installation completes.

.. note::

    If the installation process fails during the DHCP configuration step, it is most likely because your robot does not have internet access, even if you have connected an ethernet cable between the robot's computer and an internet source (e.g. router). During the Ubuntu installation process, only one (of possibly several) ethernet ports on the robot's computer can establish internet connection, so simply switch the ethernet cable to a different port and retry the DHCP configuration step.

Once the robot is powered off, remove the USB drive and turn the robot back on. You are now ready to restore your backed-up ROS Melodic data as ROS Noetic data.

Upgrading Jetson
-----------------

Clearpath's OS installation ISOs are not suitable for use on the Nvidia Jetson. If your robot uses a Jetson board (e.g. the Jetson TX2), you should download the latest version of `Nvidia's SDK Manager <https://developer.nvidia.com/nvidia-sdk-manager>`_ and follow `Nvidia's instructions <https://docs.nvidia.com/sdk-manager/install-with-sdkm-jetson/index.html>`_ to reinstall the OS on the board.

Once you have reinstalled the OS you can proceed to restoring your backed-up data.