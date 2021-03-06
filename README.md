Linux kernel
============

There are several guides for kernel developers and users. These guides can
be rendered in a number of formats, like HTML and PDF. Please read
Documentation/admin-guide/README.rst first.

In order to build the documentation, use ``make htmldocs`` or
``make pdfdocs``.  The formatted documentation can also be read online at:

    https://www.kernel.org/doc/html/latest/

There are various text files in the Documentation/ subdirectory,
several of them using the Restructured Text markup notation.

Please read the Documentation/process/changes.rst file, as it contains the
requirements for building and running the kernel, and information about
the problems which may result by upgrading your kernel.

## Heracleia Kernel
This is the heracleia kernel (Liquorix + Intel Realsense Patch). This kernel is released to reduce dependence on launchpad, which
recently removed packages for Xenial. While that's a smart thing to do, but I have to use Xenial, so I am making this own kernel for myself

## Ways to build your own liquorix kernel
The main source for the liquorix kernel is the original [linux kernel by torvalds](https://github.com/torvalds/linux). To find the version that the liquorix
kernel patches find the edits made to Makefile in the patch file at linux-liquorix/debian/patches/zen in your inetersted liquorix version at [liquorix package](https://github.com/damentz/liquorix-package). Then download original kernel source code, paste the patch file you obtained from linux-liquorix/debian/patches/zen in the kernel source root and then execute
 > patch -p1 < LIQUORIX_PATCH_FILE

 This one hosts the kernel 5.8.17-lqx2 code named "Tea Storm".

## Build Instruction
> sudo apt-get install build-essential bc curl ca-certificates fakeroot gnupg2 libssl-dev lsb-release libelf-dev bison flex zstd
Install above requirements

> make menuconfig
It will open menuconfig, don't change anything, press tab and save it. It will save the .config in your folder

> make-kpkg clean
> fakeroot make-kpkg --initrd kernel_image kernel_headers -j12
 This will create 2 debs: linux-headers-xxxxxxxxx.deb and linux-imge-xxxxxxxxx.deb. Install both of them by using `sudo dpkg -i DEB_NAME`