Restoring Your Backed-Up Data
==============================

After installing the upgraded Ubuntu 20.04 OS with ROS Noetic, you are now ready to restore the ROS Melodic data you backed up from your robot. Copy the ``.tar.gz`` file you created earlier and the ``upgrade.sh`` script from the ``robot-backup`` git repository onto the robot.

Log into the robot and run

.. code-block:: bash

    bash upgrade.sh <backup-name>

For example, if your backup file is called ``melodic-final-backup.tar.gz``, you would run:

.. code-block:: bash

  bash upgrade.sh melodic-final-backup.tar.gz

The ``upgrade.sh`` script will install the ROS Noetic versions of any ROS Melodic packages as well as doing an in-place upgrade of configuration files (e.g. ``.bashrc`` and ``/etc/ros/setup.bash``).

The script will prompt you whether or not you want to (re-)install ``apt`` and ``pip`` packages.  If you select "no" then scripts in the user's home folder will be generated to let you install them later.

.. note::

  Some ``pip`` packages may be provided by ``apt`` packages. If you select "no" when asked to install ``apt`` packages you should also select "no" to install ``pip`` packages. We recommend always installing ``apt`` packages before installing ``pip`` packages.

If ``upgrade.sh`` encounters errors installing any ``apt`` or ``pip`` packages it will create ``$HOME/could_not_install_apt.sh`` and/or ``$HOME/could_not_install_pip.sh`` files as appropriate.  Some failures are normal, as Ubuntu packages may have been removed or renamed between Ubuntu 18.04 and Ubuntu 20.04.

.. note::

  The ``upgrade.sh`` script will not take care of migrating cloned packages in your ``catkin`` workspace(s) from ROS Melodic to ROS Noetic. Typically this process is as simple as traversing into each package folder in your workspace, doing a ``git checkout`` of the ROS Noetic-specific branch for each package, and rebuilding the workspace. Ultimately, it is up to the user to manually migrate any packages in the ``catkin_ws`` workspace(s), which were previously installed from source.

Restoring Network configuration
--------------------------------

Robots running Ubuntu 20.04 with ROS Noetic use a software called ``netplan`` to configure networking. Any ``netplan`` network configuration files are located in ``/etc/netplan``. Robots running Ubuntu 18.04 with ROS Melodic should also be like this.

However, some robots running Ubuntu 18.04 with ROS Melodic **may** use the ``/etc/network/interfaces`` file to configure networking instead of using ``/etc/netplan``. If this is the case, using the ``upgrade.sh`` script will create a problem on the robot, where the restored ``/etc/network/interfaces`` file will conflict with the expected networking configurations files in ``/etc/netplan``.

If your robot falls under this special case, then after upgrading the OS, the solution is to delete the ``/etc/network/interfaces`` file and create a ``.yaml`` file in ``/etc/netplan`` that implements the same networking configuration details. It is ultimately up to you to verify if your Ubuntu 18.04 with ROS Melodic robot is using ``/etc/network/interfaces`` or ``/etc/netplan``. If the former, it is up to you to port your networking configuration to ``netplan`` after upgrading to Ubuntu 20.04 with ROS Noetic.

Restoring Non-Standard Data
----------------------------

If you manually backed up any additional files from your Melodic robot, you can restore those files at this point. Simply copy the old files to their appropriate locations on the robot.

If you created additional user accounts on the robot you can re-create those with the ``adduser`` command.
