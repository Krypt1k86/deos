# [JK2MV](https://jk2mv.org)

JK2MV (Multi Version) is a modification for Jedi Knight II: Jedi Outcast.
It supports all three game versions and comes with various features and
optimizations.

## Features

* Supports 1.02, 1.03 & 1.04 in a single executable
* Supports most mods made for JK2 (maps, skins, (code)mods etc.)
* Fast ingame HTTP-Downloads with a dialogue asking you for permission before
  downloading files to your computer
* Multiplatform: Windows, Linux, MacOSX, FreeBSD
* Multiarchitecture: 32 and 64 bit support on all platforms
* Dynamic glow: Improved lightsabers with the dynamic glow feature from JKA
* EAX/OpenAL sound fixed
* Support for modern screen resolutions
* Fixes for all known security bugs
* Minimizer: Press the Windows key / Command key in fullscreen mode to minimize
* Improved gamma correction
* Tons of other fixes and improvements in the engine, see the changelog for
  detailed information
* Opensource (GPLv2)

## Building

### 1. Clone the JK2MV repository

Clone the JK2MV repository including submodules (required if you also want to
build the [mvsdk](https://github.com/mvdevs/mvsdk) modules), e.g.:

	git clone --recursive https://github.com/mvdevs/jk2mv

### 2. Install [CMake](https://cmake.org)

### 3. Dependencies
 	
#### Windows

Requires at least Visual Studio 2013, required libraries are shipped with JK2MV
in the `libs` directory. If you plan to build the installer package get NSIS
from <http://nsis.sourceforge.net>.

#### Linux/FreeBSD

OpenGL, OpenAL, SDL2 and depending on your configuration libjpeg, libpng,
libminizip, zlib
		
##### Ubuntu/Debian

1. `apt-get install git debhelper devscripts libsdl2-dev libgl1-mesa-dev`
2. `apt-get install libopenal-dev libjpeg8-dev libpng12-dev zlib1g-dev`
3. `apt-get install libminizip-dev`

##### Fedora
	
1. `dnf install git SDL2-devel mesa-libGL-devel openal-soft-devel`
2. `dnf install libjpeg-turbo-devel libpng-devel zlib-devel minizip-devel`

#### macOS

XCode on MacOSX >= 10.6

##### Build SDL2

1. `curl -O https://www.libsdl.org/release/SDL2-2.0.8.tar.gz`
2. `tar xzf SDL2-2.0.8.tar.gz && cd SDL2-2.0.8/Xcode/SDL`
4. `sed -i -e 's/@rpath//g' SDL.xcodeproj/project.pbxproj` /* else pkg fails */
5. `xcodebuild -configuration Release`
6. `mkdir -p ~/Library/Frameworks/`
7. ``ln -s `pwd`/build/Release/SDL2.framework ~/Library/Frameworks``

##### Configuration

Use the CMake GUI to configure JK2MV or generate the default configuration by
using the build scripts in the `build` directory.

Important Options:

* `BuildPortableVersion` Build portable version (does not read or write files
                         from your user/home directory)
* `BuildMVMP` Whether to create targets for the client (jk2mvmp & jk2mvmenu)
* `BuildMVDED` Whether to create targets for the dedicated server (jk2mvded)
* `BuildMVSDK` Whether to build and integrate the mvsdk modules.
* `CMAKE_BUILD_TYPE=Debug/Release` Build for development/release.

##### Building
	
* `make` Build all previously selected binaries.
* `make install` Installs JK2MV to `/usr` on Linux. On MacOSX it finishes
                 the App-Package.
* `make package` Generates rpm/deb packages on Linux and a dmg image on MacOSX.

## License

JK2MV is licensed under GPLv2 as free software. You are free to use, modify and
redistribute JK2MV following the terms in the LICENSE file. Please be aware of
the implications of the GPLv2 licence. In short, be prepared to share your code
under the same GPLv2 licence.

## Credits

* [`openjk`](https://github.com/JACoders/OpenJK) : SDL port, engine fixes,
                                                   improvements etc.
* [`ioq3`](https://github.com/ioquake/ioq3/) : SDL port, x64 qvm, engine fixes,
                                               improvements etc.
* [`xLAva`](https://github.com/xLAva/JediOutcastLinux) : openal fixes
* [`Thoroughbred-Of-Sin`](http://thoroughbred-of-sin.deviantart.com/) : icon

---
