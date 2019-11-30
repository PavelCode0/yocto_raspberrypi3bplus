# yocto_raspberrypi3bplus
Settings for creating Linux(Yocto) for Raspberry Pi 3 B+.

Host - Debian GNU/Linux 10 (buster)

$ sudo apt-get install gawk wget git-core diffstat unzip texinfo gcc-multilib \
build-essential chrpath socat cpio python python3 python3-pip python3-pexpect \
xz-utils debianutils iputils-ping python3-git python3-jinja2 libegl1-mesa libsdl1.2-dev \
pylint3 xterm

$ mkdir yocto
$ cd yocto

$ git clone git://git.yoctoproject.org/poky
$ git clone git://git.openembedded.org/meta-openembedded
$ git clone git://git.yoctoproject.org/meta-raspberrypi

$ source poky/oe-init-build-env yocto_raspberrypi3bplus

$ bitbake-layers add-layer ../meta-openembedded/meta-oe
$ bitbake-layers add-layer ../meta-openembedded/meta-python
$ bitbake-layers add-layer ../meta-openembedded/meta-multimedia 
$ bitbake-layers add-layer ../meta-openembedded/meta-networking
$ bitbake-layers add-layer ../meta-openembedded/meta-gnome
$ bitbake-layers add-layer ../meta-openembedded/meta-xfce 
$ bitbake-layers add-layer ../meta-raspberrypi

.../yocto/yocto_raspberrypi3bplus/conf/local.conf :

MACHINE ?= "raspberrypi3-64"
PACKAGE_CLASSES ?= "package_deb"

SSTATE_MIRRORS = "\
     file://.* http://sstate.yoctoproject.org/dev/PATH;downloadfilename=PATH \n \
     file://.* http://sstate.yoctoproject.org/2.7/PATH;downloadfilename=PATH \n \
     file://.* http://sstate.yoctoproject.org/3.0/PATH;downloadfilename=PATH \n \
     "
BB_NUMBER_THREADS = "10"
     
