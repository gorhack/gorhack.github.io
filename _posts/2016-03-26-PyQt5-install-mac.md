---
layout: post
title: "Installing PyQt5 on Mac OS X"
author: "Kyle Gorak"
date: "2016/03/26"
output:
  html_document:
    keep_md: true
comments: True
tags: [Python 3, Python, development environment, GUI]
---

I am learning how to use [PyQt](https://riverbankcomputing.com/software/pyqt/intro) to create a Python GUI. These are the steps in installing PyQt5 on Mac OS X. I am running El Capitan 10.11.4 with [Homebrew](http://brew.sh).

#### Downloading pre-requisites

- Create a [virtual environment]({% post_url 2016-01-08-using-virtualenvs %})
    - `$ mkvirtualenv my_app -ppython3.5`
    - `$ workon my_app`
    - `$ mkdir my_app`
- Download [SIP](https://www.riverbankcomputing.com/software/sip/download)
- Download [PyQt](https://www.riverbankcomputing.com/software/pyqt/download5)
- Move unarchived SIP and PyQt folders to your project folder
    - `$ tar -xzf [tar file]` or use Archive Utility

#### Installing PyQt

You must install SIP prior to installing PyQt.

- Installing SIP
    - `$ cd sip-4.17/`
    - `$ python configure.py`
    - `make`
    - `make install`
    - Test the installation
        - `$ python`
        - `>>> import sip`
        - `>>> sip.SIP_VERSION_STR` should equal '4.17'
    - Delete the SIP directory
- Installing PyQt
    - `$ brew install pyqt5`
    - `$ brew linkapps qt5`
    - `$ cd PyQt-gpl-5.5.1/`
    - `$ python configure.py --qmake /usr/local/opt/qt5/bin/qmake`
    - `make`
    - `make install`
    - Test the installation
        - `$ python`
        - `>>> from PyQt5 import QtCore`
        - `>>> QtCore.QT_VERSION_STR` should equal '5.6.0'
        - `>>> from PyQt5 import Qt`
        - `>>> Qt.PYQT_VERSION_STR` should equal '5.5.1'
    - Delete the PyQt directory

#### Creating your first project

PyQt5 [Documentation](http://pyqt.sourceforge.net/Docs/PyQt5/class_reference.html) and a simple hello world application to get you started:

{% gist mizki9577/6856389 helloqt.py %}

![Hello World!]({{ site.url }}/assets/images/pyqt-hello.png){: .center-image}