# Lyli

**NOTE: This currently does build, but you must install libusbpp manually and provide appropriate environment variables to link against it. Instructions for this coming soon.**

Lyli (*Ly*tro *Li*nux) aims to provide an open source alternative to the Lytro Desktop. Currently, it allows to download images from the camera (in their .raw and .json form), and perform basic calibration.

The application has been tested only with the 1st generation Lytro camera.

[![Build Status](https://travis-ci.org/martin-pr/lyli.svg?branch=master)](https://travis-ci.org/martin-pr/lyli) [![Codacy Badge](https://api.codacy.com/project/badge/Grade/85803e0b79d64c749038696d4e4512ad)](https://www.codacy.com/app/martin.prazak/lyli?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=martin-pr/lyli&amp;utm_campaign=Badge_Grade)

## Compiling
### Requirements
* c++14 enabled compiler - tested with gcc 4.9
* libusb 1.0
* Qt 5 (Qt5Core, Qt5Widgets) - tested with Qt 5.4, required for GUI
* OpenCV

### Compilation
To obtain the sources, you can either use mercurial to clone the repository, or you can download the repository snapshot from [downloads](https://bitbucket.org/stativ/lyli/downloads).

Lyli uses CMake-based build. To compile Lyli from sources, first cd into the directory with sources and execute the following commands
~~~
mkdir build
cd build
cmake ..
make
~~~

If everything goes well, there should be a *lyli* executable in the build directory and *lyli-qt* in build/ui in case the Qt GUI was compiled.

## Usage
Lyli requires direct access to the USB bus. This can be achieved either by running Lyli as root (not recommended), or by putting the provided `51-lytro.rules` to `/etc/udev/rules.d/` which enables non-root access to the camera.

```
sudo cp 51-lytro.rules /etc/udev/rules.d/
sudo udevadm control --reload-rules
```

There are two binaries build:

* _lyli_ - can be found in the top-level build directory, it provides basic command line access to camera

* _lyli-qt_ - GUI application that is build only if the required Qt5 packages are present. Provides most of the features

## License
Most of the Lyli is licensed under LGPL v3, only the Qt GUI (in the ui/ subdirectory)
is licensed under GPL v3.

