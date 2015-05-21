#Compiling the Multi-Worm Tracker on Windows

##Compiling the C++ code to produce MWT.dll

### Overview

The authors of the Multi-Worm Tracker do all of their C++ code development under Linux.  The recommended way to compile the MWT.dll file is to cross-compile on Linux.  It is also possible to compile under windows, as follows:

* Install MinGW
* Set the path for MinGW
* Run make

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
c:\MinGW\bin\mingw32-c++
```

into a command prompt and get back

```
Mingw32-c++: fatal error: no input files
compilation terminated.
```

### Setting the MinGW path

### Compiling the MWT

By default, MinGW does _not_ set up the path properly 

First, you must make sure the makefile points to where your installation of MinGW is.  In the file `makefile` in the `src` directory of the MWT project, check that the line starting `CC = ` points to your copy of `mingw32-g++`.

You can probably find it at `C:\MinGW\bin\mingw32-g++` (an easy way to make sure the path is correct is to grab the file and drop it into a command prompt).  If your copy isn't where `CC` says it is, edit the `CC` line and save the file.  (Do not use Notepad; it doesn't understand Unix line endings.  You might need to install a slightly more capable editor like Notepad++ or Sublime Text.)

Then open the command prompt and traverse to the src directory for the MWT project.  (It's usually easiest to type `cd ` and then drag the src folder from Windows Explorer into the command prompt window.)

Finally, assuming that MinGW was installed at `C:\MinGW`, enter

```
C:\MinGW\bin\mingw32-make
```

