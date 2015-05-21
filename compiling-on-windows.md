#Compiling the Multi-Worm Tracker on Windows

##Compiling the C++ code to produce MWT.dll

### Overview

* Install MinGW
* Run make

#### Installing MinGW

The Multi-Worm Tracker uses MinGW to compile DLLs for use on Windows.

To get MinGW, go to the MinGW web page at [http://mingw.org/](http://mingw.org/) and click on the "Download Installer" button.  This will not download an installer for MinGW itself, but rather an installer installer!  Run it, and you'll get a "MinGW Installation Manager" program.  From that, select

  * mingw-developer-toolkit
  * mingw32-base
  * mingw-gcc-g++
  * msys-base

A little arrow will appear on top of each item that's selected for installation.  (Depending on the order in which you select them, some may be selected automatically for you.  If you see a very long list, you probably have "All Packages" selected on the list; pick "Basic Setup" to make it easier to find the things you need.)

Then, under the **Installation** menu (top left) select "Apply"; a window will pop up saying it's going to download some large number of things (109 as of this writing).  Click the "Apply" button on this new window and it will proceed to download the packages; this will take a couple minutes on a fast connection, plus a couple more to install the packages once they're downloaded.

