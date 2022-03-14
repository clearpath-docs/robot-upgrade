Upgrading from Melodic to Noetic
====================================

In early 2020 Clearpath Robotics added support for ROS Melodic running on Ubuntu 18.04 to our line of robots.  New
robots will ship with Ubuntu 18.04 and ROS Melodic pre-installed, but older robots may also be upgraded.

.. warning::

    It is the user's responsibility to ensure that any essential files are properly backed-up before upgrading their
    robot.

The process for upgrading your robot is to first back everything up, then reinstall the robot's OS, and finally
restore your backed-up data.

.. toctree::
    :titlesonly:
    :caption: Contents

    Overview <self>
    create-backup
    upgrade-os
    restore-backup
