# Pintos-OS
Pintos is an educational operating system for the x86. Pintos was developed for Stanford's CS 140 operating systems course.

Official website of Pintos-OS is [pintos-os.org](pintos-os.org).
To know more about the operating system and projects related to it, visit [http://courses.mpi-sws.org/os-ss13/assignments/pintos/pintos.html](http://courses.mpi-sws.org/os-ss13/assignments/pintos/pintos.html).

This version of Pintos-OS is froked from **git://pintos-os.org/pintos-anon**.
You can also view the Stanford git repository of Pintos-OS using their web CGI [http://pintos-os.org/cgi-bin/gitweb.cgi](https://www.qemu.org/download/).

## Getting Started
There are two branches for the base operating system (without the project code): `master` and `configured`.
The unmodified fork of the original repository is in the `master` branch.
The version modified to use QEMU with other relevant modifications is in the `configured` branch.

* Start by cloning the code base to your machine. This will clone both branches and checkout to `master` branch. 
```
git clone https://github.com/shreyanshkuls/CS310-pintos.git
```

* If you want to directly clone the `configured` branch only, use the command bellow and directly skip to [Build](#build).
```
git clone --single-branch --branch configured https://github.com/shreyanshkuls/CS310-pintos.git
```

## Configure
Following these steps will configure the operating system to use QEMU for emulation for linux systems.

* Navigate to `CS310-pintos/src/threads`, open `Make.vars` in a text editor and change line 7 to `SIMULATOR = --qemu`.
* Now navigate to `CS310-pintos/src/utils` and edit `pintos-gdb` by changing the line 4 to `GDBMACROS=../misc/gdb-macros`.
* In the same directory, edit the file `pintos` by changing:
	- Line 103 to `$sim = "qemu" if !defined $sim;`
	- Line 621 to `my (@cmd) = ('qemu-system-x86_64');`
* Modify `squish-pty.c` file by commenting
	- Line 10
	- Line 288-293 (both inclusive)
* Comment Line 11 in `squish-unix.c`

## Build
Before building the system, make sure to add the path to `pintos` in the `PATH` variable so that tests can be run as soon as the system is built. You can do so by adding this line in the '~/.bashrc' file.
```
export PATH="<path to directory>/CS310-pintos/src/utils:$PATH"
```

* Change the directory to `CS310-pintos/src/utils` and run `make`. This will compile the utilities in the folder.
* Navigate to `CS310-pintos/src/threads` and run `make`. This will compile the kernel and make a new directory `build` in the current directory.

## Run
You can check if the Pintos-OS is installed properly by running the following command in the `CS310-pintos/src/threads` directory.
```
pintos run alarm-multiple
```
