Upgrading from Melodic to Noetic
=================================

Clearpath Robotics' robots ship with Ubuntu 20.04 and ROS Noetic pre-installed, but robots running older software may also be upgraded. This tutorial details how to upgrade a robot running Ubuntu 18.04 with ROS Melodic to Ubuntu 20.04 with ROS Noetic.

.. warning::

    It is the user's responsibility to ensure that any essential files are properly backed-up before upgrading their robot.

The process for upgrading your robot is to first back up the important ROS Melodic files, then upgrade your robot's OS from Ubuntu 18.04 with ROS Melodic to Ubuntu 20.04 with ROS Noetic, and finally restore your backed-up ROS Melodic files as ROS Noetic files.

.. toctree::
    :titlesonly:
    :caption: Contents

    Overview <self>
    create-backup
    upgrade-os
    restore-backup
