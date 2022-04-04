# robot-upgrade

Tutorial for upgrading robots from Ubuntu 18.04 with ROS Melodic to Ubuntu 20.04 with ROS Noetic.

## Cloning

To clone this repository simply run

    git clone --recursive https://github.com/clearpath-docs/robot-upgrade.git

## Prerequisites

To build this guide you must have sphinx installed via `pip`:

    pip3 install sphinx

## Building

To build the docs cd into the root folder of the repository and run the following commands:

    mkdir html
    sphinx-build -b html doc html

If you get errors about missing fonts, go to latex/clearpath-latex/fonts and install all the fonts there
