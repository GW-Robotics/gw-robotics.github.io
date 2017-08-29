+++
title = "HOW-TO: OpenCV Installation (Windows)"
date = "2016-11-08T14:37:34"
tags = ["opencv", "vision"]
categories = ["control-systems"]
+++

This tutorial is for installation of OpenCV for Python on a Windows PC from prebuilt files. A fully detailed tutorial can be found [at the OpenCV documentation](http://docs.opencv.org/3.0-beta/doc/py_tutorials/py_setup/py_setup_in_windows/py_setup_in_windows.html#install-opencv-python-in-windows).

## To Install OpenCV and Dependencies

First, make sure that your computer has the right Python setup with Numpy. Matplotlib is optional and is mostly for use with the tutorials. You can check that you have Python 2.7.whatever using:

```bash
python -V
```

After verifying that you have Python 2.7, you can install the packages using Pip using:

```bash
pip install numpy
pip install matplotlib
```

Next, download the OpenCV installer from [here](https://sourceforge.net/projects/opencvlibrary/?source=typ_redirect). Double-click and run it. Then navigate to the extracted folder opencv/build/python/2.7/x86 and move "cv2.pyd" to C:/Python27/lib/site-packages.

## To Verify Your Installation

Type the following command:

```bash
python
```

This opens the Python Interpreter, where you can type the following and run:

```python
import numpy; import cv2; print cv2.__version__
```

If it runs with no errors, then everything was installed correctly!