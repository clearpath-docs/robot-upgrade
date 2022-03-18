Upgrading from Melodic to Noetic
=================================

Clearpath Robotics' robots ship with Ubuntu 20.04 and ROS Noetic pre-installed, but robots running older software may also be upgraded. This tutorial details how to upgrade a robot running Ubuntu 18.04 and ROS Melodic to Ubuntu 20.04 and ROS Noetic.

.. warning::

    It is the user's responsibility to ensure that any essential files are properly backed-up before upgrading their robot.

The process for upgrading your robot is to first back everything up, then reinstall the robot's OS with the upgraded OS, and finally restore your backed-up data.

.. toctree::
    :titlesonly:
    :caption: Contents

    Overview <self>
    create-backup
    upgrade-os
    restore-backup
