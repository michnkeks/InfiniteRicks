![alt text](http://infiniteblocks.space/images/logo.png)  
                
                
                
                
                           Multiverse Cryptocurrency InfiniteRicks

Type	PoS

Coin name	InfiniteRicks

Coin abbreviation	RICK


Address letter	1

Min stake age 12 Hours

Block time 2 min

APR  307% a year

RPC port	31648

P2P port	31647



Blockexplorer 
http://infiniteblocks.space

Official Website 
https://infinitericks.space/








InfiniteRicks development tree

InfiniteRicks is a PoS-based cryptocurrency.

Development process
===========================

Developers work in their own trees, then submit pull requests when
they think their feature or bug fix is ready.

The patch will be accepted if there is broad consensus that it is a
good thing.  Developers should expect to rework and resubmit patches
if they don't match the project's coding conventions (see coding.txt)
or are controversial.

The master branch is regularly built and tested, but is not guaranteed
to be completely stable. Tags are regularly created to indicate new
stable release versions of InfiniteRicks.

Feature branches are created when there are major new features being
worked on by several people.

From time to time a pull request will become outdated. If this occurs, and
the pull is no longer automatically mergeable; a comment on the pull will
be used to issue a warning of closure. The pull will be closed 15 days
after the warning if action is not taken by the author. Pull requests closed
in this manner will have their corresponding issue labeled 'stagnant'.

Issues with no commits will be given a similar warning, and closed after
15 days from their last activity. Issues closed in this manner will be 
labeled 'stale'.

InfiniteRicks-qt: Qt5 GUI for InfiniteRicks

Build instructions

Debian

First, make sure that the required packages for Qt5 development of your distribution are installed, for Debian and Ubuntu these are:

apt-get install qt5-default qt5-qmake qtbase5-dev-tools qttools5-dev-tools \
    build-essential libboost-dev libboost-system-dev \
    libboost-filesystem-dev libboost-program-options-dev libboost-thread-dev \
    libssl-dev libdb++-dev

 This Step is needed as well
 sudo apt-get install libqt4-dev libminiupnpc-dev
then execute the following:

qmake
make
Alternatively, install Qt Creator and open the InfiniteRicks-qt.pro file.

An executable named InfiniteRicks-qt will be built.

Windows

Windows build instructions:

Download the QT Windows SDK and install it. You don't need the Symbian stuff, just the desktop Qt.
Compile openssl, boost and dbcxx.
Open the .pro file in QT creator and build as normal (ctrl-B)
Mac OS X

Download and install the Qt Mac OS X SDK. It is recommended to also install Apple's Xcode with UNIX tools.
Download and install MacPorts.
Execute the following commands in a terminal to get the dependencies:
sudo port selfupdate
sudo port install boost db48 miniupnpc
Open the .pro file in Qt Creator and build as normal (cmd-B)
Build configuration options

UPNnP port forwarding

To use UPnP for port forwarding behind a NAT router (recommended, as more connections overall allow for a faster and more stable InfiniteRicks experience), pass the following argument to qmake:

qmake "USE_UPNP=1"
(in Qt Creator, you can find the setting for additional qmake arguments under "Projects" -> "Build Settings" -> "Build Steps", then click "Details" next to qmake)

This requires miniupnpc for UPnP port mapping. It can be downloaded from http://miniupnp.tuxfamily.org/files/. UPnP support is not compiled in by default.

Set USE_UPNP to a different value to control this:

USE_UPNP=-	no UPnP support, miniupnpc not required;
USE_UPNP=0	(the default) built with UPnP, support turned off by default at runtime;
USE_UPNP=1	build with UPnP support turned on by default at runtime.
Notification support for recent (k)ubuntu versions

To see desktop notifications on (k)ubuntu versions starting from 10.04, enable usage of the FreeDesktop notification interface through DBUS using the following qmake option:

qmake "USE_DBUS=1"
Generation of QR codes

libqrencode may be used to generate QRCode images for payment requests. It can be downloaded from http://fukuchi.org/works/qrencode/index.html.en, or installed via your package manager. Pass the USE_QRCODE flag to qmake to control this:

USE_QRCODE=0	(the default) No QRCode support - libarcode not required
USE_QRCODE=1	QRCode support enabled
Berkely DB version warning

A warning for people using the static binary version of InfiniteRicks on a Linux/UNIX-ish system (tl;dr: Berkely DB databases are not forward compatible).

The static binary version of InfiniteRicks is linked against libdb 5.0 (see also this Debian issue).

Now the nasty thing is that databases from 5.X are not compatible with 4.X.

If the globally installed development package of Berkely DB installed on your system is 5.X, any source you build yourself will be linked against that. The first time you run with a 5.X version the database will be upgraded, and 4.X cannot open the new format. This means that you cannot go back to the old statically linked version without significant hassle!

Ubuntu 11.10 warning

Ubuntu 11.10 has a package called 'qt-at-spi' installed by default. At the time of writing, having that package installed causes InfiniteRicks-qt to crash intermittently. The issue has been reported as launchpad bug 857790, but isn't yet fixed.

Until the bug is fixed, you can remove the qt-at-spi package to work around the problem, though this will presumably disable screen reader functionality for Qt apps:

sudo apt-get remove qt-at-spi
