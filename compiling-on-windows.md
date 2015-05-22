#Compiling the Multi-Worm Tracker on Windows

##Compiling the C++ code to produce MWT.dll

### Overview

The authors of the Multi-Worm Tracker do all of their C++ code development under Linux.  The recommended way to compile the MWT.dll file is to cross-compile on Linux.  It is also possible to compile under windows, as follows:

* Install MinGW (do once)
* Set the path for MinGW (do every time you open a command window)
* Run make (every time you want to create a new MWT.dll)

### Installing MinGW

The Multi-Worm Tracker uses MinGW to compile DLLs for use on Windows.

To get MinGW, go to the MinGW web page at [http://mingw.org/](http://mingw.org/) and click on the "Download Installer" button.  This will not download an installer for MinGW itself, but rather an installer installer!  Run it, and you'll get a "MinGW Installation Manager" program.  From that, select

  * mingw-developer-toolkit
  * mingw32-base
  * mingw-gcc-g++
  * msys-base

A little arrow will appear on top of each item that's selected for installation.  (Depending on the order in which you select them, some may be selected automatically for you.  If you see a very long list, you probably have "All Packages" selected on the list; pick "Basic Setup" to make it easier to find the things you need.)

Then, under the **Installation** menu (top left) select "Apply"; a window will pop up saying it's going to download some large number of things (109 as of this writing).  Click the "Apply" button on this new window and it will proceed to download the packages; this will take a couple minutes on a fast connection, plus a couple more to install the packages once they're downloaded.

If all goes correctly, you should be able to type

```
C:\MinGW\bin\mingw32-c++
```

into a command prompt and get back

```
Mingw32-c++: fatal error: no input files
compilation terminated.
```

If this doesn't work, perhaps MinGW didn't get installed in the default location--replace `C:\MinGW` with the correct path.

### Setting the MinGW path

Open a command window that you will use to compile the MWT.  Enter

```
set PATH=%PATH%;C:\MinGW\bin
```

(assuming that MinGW was installed in the default location--drag the correct `bin` directory after the `;` if it was installed somewhere else).

To test that this worked, try typing `mingw32-c++`.  It should give you the same fatal error message as the one above.

You'll need to do this every time you open a new command window--MinGW does not set the system path itself, so it's effectively unusable unless this is done.

### Compiling the MWT with make

Once you have set the path, src directory for the MWT project.  (It's usually easiest to type `cd ` and then drag the src folder from Windows Explorer into the command prompt window.)

Enter

```
mingw32-make DLL
```

(DLL must be in all caps).

You should see a bunch of lines like

```
C:\MinGW\bin\mingw32-g++ -Wall -O2 -fno-strict-aliasing -ggdb3 -shared -DUNIT_TEST_OWNER -DWINDOWS  -o unit_geometry MWT_Geometry.cc
```

and possibly some warning messages talking about `[-Wreorder]`.

You should see a newly created (or re-created) file in the `lib` directory, `MWT.dll`.

It is recommended that you copy this file somewhere else before you tell the LabView VIs where to find it, so you are less likely to accidentally create a new MWT.dll over the one that the MWT (if running) is already using.  This generally does not work well.

That's it!

----

This this document is copyright (c) Rex Kerr and HHMI Janelia, 2015.
It is distributed under [CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/), the Creative Commons 4.0 Attribution-ShareAlike license.