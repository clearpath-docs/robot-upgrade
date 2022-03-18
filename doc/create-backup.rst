Backing Up Your Robot's Data
=============================

It is always a good idea to keep any customized configuration files or project source code backed up. This is especially true when upgrading your robot from ROS Melodic to ROS Noetic, as this process will wipe the robot's internal storage.

Download the Backup Software
-----------------------------

Clearpath Robotics provides a package containing several shell scripts to help you back up, upgrade, and/or restore your robot's most important data. You can download a copy of this script by running the following command on your computer:

.. code-block:: bash

    git clone https://github.com/clearpathrobotics/robot-backup

Follow the instructions in the ``robot-backup/README.md`` file to ensure you have all of the prerequisites installed.

Running the Backup Script
--------------------------

Ensure that the robot is turned on and that you can SSH into it from your computer. Then run the following from your computer:

.. code-block:: bash

    cd robot-backup
    bash backup.sh <backup-name> <hostname|IP address of the robot>

For example, if your robot's IP address is 192.168.1.103, you would run something like

.. code-block:: bash

    bash backup.sh melodic-final-backup 192.168.1.103

This will produce a backup file called ``melodic-final-backup.tar.gz``. Keep this file for when you need to restore your backed-up data.

By default all Clearpath robots use the username "administrator" and the password "clearpath".  The ``backup.sh`` script will use these credentials by default, but you can override them easily.

For example, if your robot has been modified to use an Nvidia Jetston TX2, the username and password will both be "nvidia". In this case, you should run

.. code-block:: bash

  bash backup.sh melodic-final-backup nvidia@192.168.1.103 nvidia

What Gets Backed Up
--------------------

The backup script will copy the following data:

- Home Folder: ``~/``
- ``udev`` Rules: ``/etc/udev/rules.d``
- Network Setup:
  - ``/etc/network/interfaces``
  - ``/etc/netplan``
  - ``/etc/hostname``
  - ``/etc/hosts``
- IP Tables: ``/etc/iptables``
- Bringup Files:
  - ``/etc/ros/setup.bash``
  - ``/etc/ros/$ROSDISTRO/ros.d``
  - ``/usr/sbin/*start``
  - ``/usr/sbin/*stop``
- ``rosdep`` sources: ``/etc/ros/rosdep``
- ``rc.local`` File: ``/etc/rc.local``
- ``pip`` packages
- ``systemd`` configuration: ``/etc/systemd/system``
- ``apt`` sources: ``/etc/apt/sources.list.d``
- ``apt`` packages
- User Permission Groups

Backing Up Non-Standard Data
-----------------------------

The ``backup.sh`` script assumes that your robot is in a roughly-standard configuration; it uses a single user account and no files within ``/opt/ros/melodic`` have been modified.

If this is **not** the case, it is the responsibility of the user to ensure that any modified files and files in other users' home folders is backed up correctly.

A common example of this might be if you have created customized URDF files to be loaded via environment variables (e.g. ``JACKAL_URDF_EXTRAS``) and have stored them outside any of the folders specified above, you must back these up yourself; ``backup.sh`` will not do this for you.