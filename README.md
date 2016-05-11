Kindle Touch Terminal
=====================

KTTerm is a terminal emulator for Kindle Touch device. It is based on the GTK+ terminal emulator
widget - [VTE](https://github.com/GNOME/vte).

KTTerm supports standard `-e` option (available in all (?) terminal emulators), which can be used
to specify the program and its command line arguments to be run in the KTTerm window. If this
option is not given, the standard command line interpreter `/bin/sh` is launched.

	$ ktterm -h
	usage: ktterm [options] [-e CMD [ args ]]
	  -K        use build-in Kindle keyboard
	  -R DIR    use DIR as a resources directory
	  -e CMD    run command with its arguments
	  -f        run in the full-screen mode
	  -r        use reversed color palette
	  -s NB     set terminal font size to NB

![Screenshot](/screenshot.png?raw=true)


Keyboard shortcuts
------------------

* `Fn` + `F` - toggle full-screen mode
* `Fn` + `R` - switch between portrait and landscape mode
* `Fn` + `plus (+)` - increase font size
* `Fn` + `minus (-)` - decrease font size
* `Fn` + `0` - restore font size

These functions are available only with the build-in keyboard.


Keyboard toggle
---------------

It is possible to hide/show keyboard by the tap-and-hold action on the upper-right corner of the
KTTerm window. This action is available for build-in and Kindle on-board keyboard.


Compilation
-----------

	$ autoreconf --install
	$ mkdir build && cd build
	$ export KINDLE_ROOTDIR=<absolute_patch_to_the_Kindle_root_directory>
	$ ../configure --enable-kindle-env --host=armv7a-softfp-linux-gnueabi
	$ make

**Note:** Enabling Kindle development environment during configuration requires static libraries
for json-c and VTE. It is possible to compile KTTerm using standard configuration, however such
an action might produce executable incompatible with libraries available on Kindle.

**Note²:** It is possible to link KTTerm against a proprietary lipc library using `--with-lipc`
flag during configuration. Otherwise, shell wrapper will be used instead.


Similar projects
----------------

1. [Kterm](http://www.fabiszewski.net/kindle-terminal/) - terminal emulator for Kindle Touch and
	 Paperwhite
