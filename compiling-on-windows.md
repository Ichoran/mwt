#Compiling the Multi-Worm Tracker on Windows

##Compiling the C++ code to produce MWT.dll

### Overview

The authors of the Multi-Worm Tracker do all of their C++ code development under Linux.  The recommended way to compile the MWT.dll file is to cross-compile on Linux.  It is also possible to compile under windows, as follows:

* Install MinGW (do once)
* Set the path for MinGW (do once)
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

To compile the MWT with LabView, you will need LabView to be able to find the MinGW DLL files, as well as for the MinGW tools to be able to find each other.  The easiest way to do this is to add `C:\MinGW\bin` path to the system path (use wherever MinGW is actually installed if not `C:\MinGW`).

**Be careful with this step.  Destroying the path information is a quick way to make your computer hard/impossible to use.**

To do this, open the Control Panel (Windows key, then select from menu).  In the top right corner there's a search box; enter `path`.  It should find one thing with three subheadings:

```
System
Edit environment variables for your account
Edit the system environment variables
```

Click on the middle of these and you should get a window called "Environment Variables".  In the bottom half of the window, under "System variables", find the line that starts with `Path` on the left.  Click `Edit...`.  It will pop up a window called "Edit System Variable".  It starts out highlighting the whole set of paths under "Variable value", as if maybe you want to delete it.

_Don't delete the existing path!_  If you mess it up, just hit `Cancel` and try again.

_Don't_ just start typing.

_Do_ click at the very end of the line; maybe you'll need to use the arrow keys to get all the way there.  Type in

```
;C:\MinGW\bin
```

at the end of the line, after everything else.  Include the semicolon, `;`.  (Be sure you're really at the end and not inserting this into the middle of some other path.)  Don't make any other changes.  Click `OK` and the path is saved.

Did you mess up?  Actually, the path is _not_ saved yet!  You also need to click `OK` on the Environment Variables window before it's really saved.  If you made a mistake, cancel that window.  Otherwise, click `OK`.  Now it's _really_ saved.

To test that this worked, open a new command window and enter `mingw32-c++`.  It should give you the same fatal error message as the one you got when testing that MinGW was installed.

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


## Compiling the MWT with LabVIEW 2014

_Note: this entire section is tentative and untested at this point._

### Setting up LabVIEW 2014

The MWT makes use of LabVIEW to handle hardware interfacing.  The following components are needed to modify the hardware- and user-interfacing parts of the MWT:

1. LabVIEW [Full Development System](http://sine.ni.com/nips/cds/view/p/lang/en/nid/212666) ([Professional](http://sine.ni.com/nips/cds/view/p/lang/en/nid/212669) required to deploy to other machines)
2. LabVIEW [Vision Acquisition Software](http://sine.ni.com/nips/cds/view/p/lang/en/nid/12892)
3. LabVIEW [Vision Development Module](http://sine.ni.com/nips/cds/view/p/lang/en/nid/209860)

LabVIEW and the Vision Development Module are expensive.  We apologize.  LabVIEW does a lot of work to make sure hardware "just works", so you're getting good value there.  The Vision Development Module provides a handful of essential but not-very-impressive capabilities for the MWT, and ought to be able to be engineered out.  Nobody's
had time yet.

### Running the MWT project in LabVIEW

(Something about loading `MultiWormTracker.lvproj`.)

(Something about making sure you have the Vision Development Module.)

### Building the MWT project for deployment on other machines

----

This this document is copyright (c) Rex Kerr and HHMI Janelia, 2015.
It is distributed under [CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/), the Creative Commons 4.0 Attribution-ShareAlike license.