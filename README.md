# Tutorial for upgrading robots from Ubuntu 16.04 + Kinetic to 18.04 + Melodic

In early 2020 Clearpath Robotics started supporting ROS Melodic running on Ubuntu 18.04 on our line of robots.  New
robots sold will begin shipping with ROS Melodic.  Older robots will require the user to upgrade them themselves.  This
is a small tutorial explaining how to do that migration.

## Cloning
To clone this repository simply run

    git clone --recursive https://github.com/clearpath-docs/robot-upgrade.git

## Prerequisites
To build this guide you must have sphinx installed via PIP:

    pip3 install sphinx

## Buiding
To build the docs cd into the root folder of the repository and run the following commands:

    mkdir html
    sphinx-build -b html doc html

If you get errors about missing fonts, go to latex/clearpath-latex/fonts and install all the fonts there
