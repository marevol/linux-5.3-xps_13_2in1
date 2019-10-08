# Linux Kernel 5.3 for Dell XPS 13 2 in 1

This repository is for My Ubuntu 18.04 environment :)
Please do this at your own risk.

## Build DEB Package for Ubuntu 18.04

### Setup

1. Uncomment the following lines in /etc/apt/source.list.

```
deb-src http://archive.ubuntu.com/ubuntu bionic main restricted #Added by software-properties
deb-src http://security.ubuntu.com/ubuntu bionic-security restricted main multiverse universe
```

2. Install packages.
```
$ sudo apt install kernel-package
$ sudo apt install git ccache fakeroot libncurses5-dev
$ sudo apt build-dep linux
```

### Build Kernel

1. Download a source code.

```
$ git clone https://github.com/marevol/linux-5.3-xps_13_2in1.git
$ cd linux-5.3-xps_13_2in1
```

2. Build a linux kernel.

```
$ sudo -s
# make-kpkg -j `nproc` --rootcmd fakeroot --initrd --append_to_version=-xps --revision=001 kernel_image kernel_headers
```

3. Install deb packages.

```
# cd ..
# dpkg -i linux-headers-5.3.2-xps_001_amd64.deb linux-image-5.3.2-xps_001_amd64.deb 
```

4. Reboot

## References

- [XPS 13 2 in 1 (7390) - Linux boot attempt](https://www.reddit.com/r/Dell/comments/cx0fkc/xps_13_2_in_1_7390_linux_boot_attempt/?sort=new)
- [Dell XPS 7390 2-in-1 Manjaro Linux Fixes](https://github.com/endeavour/DellXps7390-2in1-Manjaro-Linux-Fixes)
- [My blog](https://www.chazine.com/archives/4019) in Japanese

