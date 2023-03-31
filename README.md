# DEPRECATED - OpenWrt for CNCD project

> Use https://github.com/wireless-cnc/cncd-esp01 instead

## Pre-req

1. VoCore v1 board
2. WSL or Linux host
3. Install Rust from official website
4. Add ``mipsel-unknown-linux-musl`` target using ``rustup`` command
5. Follow the OpenWrt Build System instructions to build a firwmware using prepared config in this repo.

## Flash memory layout

    [    0.697342] 4 fixed-partitions partitions found on MTD device spi0.0
    [    0.710091] Creating 4 MTD partitions on "spi0.0":
    [    0.719666] 0x000000000000-0x000000030000 : "uboot"
    [    0.731488] 0x000000030000-0x000000040000 : "uboot-env"
    [    0.743941] 0x000000040000-0x000000050000 : "factory"
    [    0.756078] 0x000000050000-0x000001000000 : "firmware"
    [    0.776806] 2 uimage-fw partitions found on MTD device firmware
    [    0.788749] Creating 2 MTD partitions on "firmware":
    [    0.798728] 0x000000000000-0x000000124da2 : "kernel"
    [    0.810734] 0x000000124da2-0x000000fb0000 : "rootfs"
    [    0.822604] mtd: device 5 (rootfs) set to be root filesystem
    [    0.838193] 1 squashfs-split partitions found on MTD device rootfs
    [    0.850718] 0x0000003fb000-0x000000fb0000 : "rootfs_data"
    [    0.868096] spi spi1.0: force spi mode3

## How to compile

    ./scripts/feeds update packages


    ./scripts/feeds install libpam libgnutls libopenldap libidn2 libssh2 libcap liblzma libnetsnmp jansson

    make -j$(nproc) download
    make -j$(nproc) world

---
<pre>
  _______                     ________        __
 |       |.-----.-----.-----.|  |  |  |.----.|  |_
 |   -   ||  _  |  -__|     ||  |  |  ||   _||   _|
 |_______||   __|_____|__|__||________||__|  |____|
          |__| W I R E L E S S   F R E E D O M
 -----------------------------------------------------

This is the buildsystem for the OpenWrt Linux distribution.

To build your own firmware you need a Linux, BSD or MacOSX system (case
sensitive filesystem required). Cygwin is unsupported because of the lack
of a case sensitive file system.

You need gcc, binutils, bzip2, flex, python, perl, make, find, grep, diff,
unzip, gawk, getopt, subversion, libz-dev and libc headers installed.

1. Run "./scripts/feeds update -a" to obtain all the latest package definitions
defined in feeds.conf / feeds.conf.default

2. Run "./scripts/feeds install -a" to install symlinks for all obtained
packages into package/feeds/

3. Run "make menuconfig" to select your preferred configuration for the
toolchain, target system & firmware packages.

4. Run "make" to build your firmware. This will download all sources, build
the cross-compile toolchain and then cross-compile the Linux kernel & all
chosen applications for your target system.

Sunshine!
	Your OpenWrt Community
	http://www.openwrt.org

</pre>
