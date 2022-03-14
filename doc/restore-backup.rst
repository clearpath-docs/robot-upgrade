Restoring your backed-up data
================================

After installing the updated operating system you are ready to restore the data you backed up from your robot.
Copy the .tar.gz file you created earlier and the ``upgrade.sh`` script from the robot-backup git repository onto
the robot.

Log into the robot and run

.. code-block:: bash

    bash upgrade.sh <backup-name>

For example, if your backup file is called ``melodic-final-backup.tar.gz`` you would run
``bash upgrade.sh melodic-final-backup``

The ``upgrade.sh`` script will install the ROS Melodic versions of any ROS Melodic packages as well as doing an
in-place upgrade of configuration files (e.g. ``.bashrc`` and ``/etc/ros/setup.bash``).

The script will prompt you whether or not you want to (re-)install Apt and Pip packages.  If you select "no" then
scripts in the user's home folder will be generated to let you install them later.

.. note::

  Some pip packages may be provided by Apt packages.  If you select "no" when asked to install Apt packages you should
  also select "no" to install Pip packages.  We recommend always installing Apt packages before installing Pip packages.

If ``upgrade.sh`` encounters errors installing any Apt or Pip packages it will create ``$HOME/could_not_install_apt.sh``
and/or ``$HOME/could_not_install_pip.sh`` files as appropriate.  Some failures are normal, as Ubuntu packages may have
been removed or renamed between 16.04 and 18.04.


Restoring non-standard data
-------------------------------

If you manually backed up any additional files from your Melodic robot, you can restore those files at this point.
Simply copy the old files to their appropriate locations on the robot.

If you created additional user accounts on the robot you can re-create those with the ``adduser`` command.
