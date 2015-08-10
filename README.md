# Runlinux

cd into a Linux kernel source tree, run one line of bash, and get a running QEMU VM with BusyBox.

    sudo apt-get install qemu
    cd /tmp
    git clone --recursive https://github.com/cirosantilli/runlinux
	git clone git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git
	cd linux
	git checkout v4.1
	../runlinux/runlinux

It takes a while the first time, but further runs will be faster.

Then hack the kernel source to your liking, and run:

	../runlinux/runlinux

again to try it out.

Out-of-tree build with custom configuration:

    export KBUILD_OUTPUT="$(pwd)/../build"
    make menuconfig
	../runlinux/runlinux

If an existing configuration is not found, `make defconfig` is used. If found, it is used and left untouched.

Based on: <https://github.com/ivandavidov/minimal>

Tested in Ubuntu 14.04 AMD64.
