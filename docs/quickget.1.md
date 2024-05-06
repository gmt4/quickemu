---
author: Martin Wimpress
date: May 5, 2024
footer: quickget
header: Quickget User Manual
section: 1
title: QUICKGET
---

# NAME

quickget - download and prepare materials for building a quickemu VM

# SYNOPSIS

**quickget** \[*os*\] \[*release*\] \[*edition*\] \| \[*OPTION*\]\*

# DESCRIPTION

**quickget** will download the requisite materials and prepare a
configuration for `quickemu` to use to build and run

# OPTIONS

**version \| -version \| --version**
:   show version (from Quickemu)

**list \| list_csv \| list_json**
:   provide a csv list of all supported guest OSes, versions and
    variants.

**`--show-iso-url` \| -s** {**os**} {**release**} \[**edition**\]
:   show ISO download URL

**`--test-iso-url` \| -t** {**os**} {**release**} \[**edition**\]
:   test if ISO is available

**`--open-distro-homepage` \| -o** {**os**}
:   open OS homepage in browser

**\[OS\] \[Release\] \[Edition\]**
:   specify the OS and release (and optional edition) if insufficient
    input is provided a list of missing options will be reported and the
    script will exit. Editions may not apply and will be defaulted if
    not provided.

# NOTES

## Creating Linux guests 🐧

### Ubuntu

`quickget` will automatically download an Ubuntu release and create the
virtual machine configuration.

``` shell
quickget ubuntu 22.04
quickemu --vm ubuntu-22.04.conf
```

-   Complete the installation as normal.
-   Post-install:
    -   Install the SPICE agent (`spice-vdagent`) in the guest to enable
        copy/paste and USB redirection
        -   `sudo apt install spice-vdagent`
    -   Install the SPICE WebDAV agent (`spice-webdavd`) in the guest to
        enable file sharing.
        -   `sudo apt install spice-webdavd`

### Ubuntu daily-live images

`quickget` can also download/refresh daily-live images via `zsync` for
Ubuntu developers and testers.

``` shell
quickget ubuntu daily-live
quickemu --vm ubuntu-daily-live.conf
```

You can run `quickget ubuntu daily-live` to refresh your daily
development image as often as you like, it will even automatically
switch to a new series.

### Ubuntu Flavours

All the official Ubuntu flavours are supported, just replace `ubuntu`
with your preferred flavour.

The project
[wiki](https://github.com/quickemu-project/quickemu/wiki/02-Create-Linux-virtual-machines)
may have further information.

-   `edubuntu` (Edubuntu)
-   `kubuntu` (Kubuntu)
-   `lubuntu` (Lubuntu)
-   `ubuntu-budgie` (Ubuntu Budgie)
-   `ubuntucinnamon` (Ubuntu Cinnamon)
-   `ubuntukylin` (Ubuntu Kylin)
-   `ubuntu-mate` (Ubuntu MATE)
-   `ubuntu-server` (Ubuntu Server)
-   `ubuntustudio` (Ubuntu Studio)
-   `ubuntu` (Ubuntu)
-   `ubuntu-unity` (Ubuntu Unity)
-   `xubuntu` (Xubuntu)

You can also use `quickget` with advanced options :

``` text
  -[12345]              <os>           : Show info* about OS
  --download       (-d) <os> <re> [ed] : Download image; no VM configuration
  --create-config (-cc) <os> [path/url]: Create default VM config for image
  --open-homepage  (-o) <os>           : Open homepage for the OS
  --version        (-v)                : Show version
  --help           (-h)                : Show this help message
  --url            (-u) [os] [re] [ed] : Show image URL(s)
  --check          (-c) [os] [re] [ed] : Check image URL(s)
  --list           (-l)                : List all supported systems
  --list-csv      (-lc)                : List everything in csv format
  --list-json     (-lj)                : List everything in json format
```

Here are some typical uses

``` shell
    # show an OS ISO download URL for {os} {release} [edition]
    quickget --url fedora 38 Silverblue
    # test if an OS ISO is available for {os} {release} [edition]
    quickget --check nixos unstable plasma5
    # open an OS distribution homepage in a browser
    quickget --open-homepage  ubuntu-mate
    # Only download image file into current directory, without creating VM
    quickget --download elementary 7.1
```

The `--url`, `--check`, and `--download` options are fully functional
for all operating systems, including Windows and macOS.

Further information is available from the project
[wiki](https://github.com/quickemu-project/quickemu/wiki/06-Advanced-quickget-features)

### Other Operating Systems

`quickget` also supports:

-   `alma` (Alma Linux)
-   `alpine` (Alpine Linux)
-   `android` (Android x86)
-   `antix` (Antix)
-   `archcraft` (Archcraft)
-   `archlinux` (Arch Linux)
-   `arcolinux` (Arco Linux)
-   `artixlinux` (Artix Linux)
-   `athenaos` (Athena OS)
-   `batocera` (Batocera)
-   `bazzite` (Bazzite)
-   `biglinux` (BigLinux)
-   `blendos` (BlendOS)
-   `bodhi` (Bodhi)
-   `bunsenlabs` (BunsenLabs)
-   `cachyos` (CachyOS)
-   `centos-stream` (CentOS Stream)
-   `chimeralinux` (Chimera Linux)
-   `crunchbang++` (#!++)
-   `debian` (Debian)
-   `deepin` (Deepin)
-   `devuan` (Devuan)
-   `dragonflybsd` (DragonFlyBSD)
-   `easyos` (EasyOS)
-   `elementary` (elementary OS)
-   `endeavouros` (EndeavourOS)
-   `endless` (Endless OS)
-   `fedora` (Fedora)
-   `freebsd` (FreeBSD)
-   `freedos` (FreeDOS)
-   `garuda` (Garuda Linux)
-   `gentoo` (Gentoo)
-   `ghostbsd` (GhostBSD)
-   `gnomeos` (GNOME OS)
-   `guix` (Guix)
-   `haiku` (Haiku)
-   `holoiso` (SteamOS HoloISO)
-   `kali` (Kali)
-   `kdeneon` (KDE Neon)
-   `kolibrios` (KolibriOS)
-   `linuxlite` (Linux Lite)
-   `linuxmint` (Linux Mint)
-   `lmde` (Linux Mint Debian Edition)
-   `mageia` (Mageia)
-   `manjaro` (Manjaro)
-   `mxlinux` (MX Linux)
-   `netboot` (netboot.xyz)
-   `netbsd` (NetBSD)
-   `nitrux` (Nitrux)
-   `nixos` (NixOS)
-   `nwg-shell` (nwg-shell)
-   `openbsd` (OpenBSD)
-   `openindiana` (OpenIndiana)
-   `opensuse` (openSUSE)
-   `oraclelinux` (Oracle Linux)
-   `parrotsec` (Parrot Security)
-   `peppermint` (PeppermintOS)
-   `popos` (Pop!\_OS)
-   `porteus` (Porteus)
-   `primtux` (PrimTux)
-   `pureos` (PureOS)
-   `reactos` (ReactOS)
-   `rebornos` (RebornOS)
-   `rockylinux` (Rocky Linux)
-   `siduction` (Siduction)
-   `slackware` (Slackware)
-   `slax` (Slax)
-   `slint` (Slint)
-   `slitaz` (SliTaz)
-   `solus` (Solus)
-   `sparkylinux` (SparkyLinux)
-   `spirallinux` (SpiralLinux)
-   `tails` (Tails)
-   `tinycore` (Tiny Core Linux)
-   `trisquel` (Trisquel)
-   `truenas-core` (TrueNAS Core)
-   `truenas-scale` (TrueNAS Scale)
-   `tuxedo-os` (Tuxedo OS)
-   `vanillaos` (Vanilla OS)
-   `void` (Void Linux)
-   `vxlinux` (VX Linux)
-   `zorin` (Zorin OS)

### [Custom Linux guests](https://github.com/quickemu-project/quickemu/wiki/02-Create-Linux-virtual-machines#manually-create-linux-guests)

Or you can download a Linux image and manually create a VM
configuration.

-   Download a .iso image of a Linux distribution
-   Create a VM configuration file; for example `debian-bullseye.conf`

``` shell
guest_os="linux"
disk_img="debian-bullseye/disk.qcow2"
iso="debian-bullseye/firmware-11.0.0-amd64-DVD-1.iso"
```

-   Use `quickemu` to start the virtual machine:

``` shell
quickemu --vm debian-bullseye.conf
```

-   Complete the installation as normal.
-   Post-install:
    -   Install the SPICE agent (`spice-vdagent`) in the guest to enable
        copy/paste and USB redirection.
    -   Install the SPICE WebDAV agent (`spice-webdavd`) in the guest to
        enable file sharing.

## [Creating macOS Guests](https://github.com/quickemu-project/quickemu/wiki/03-Create-macOS-virtual-machines#automatically-create-macos-guests) 🍏

`quickget` automatically downloads a macOS recovery image and creates a
virtual machine configuration.

``` shell
quickget macos catalina
quickemu --vm macos-catalina.conf
```

macOS `high-sierra`, `mojave`, `catalina`, `big-sur`, `monterey`,
`ventura` and `sonoma` are supported.

-   Use cursor keys and enter key to select the **macOS Base System**
-   From **macOS Utilities**
    -   Click **Disk Utility** and **Continue**
        -   Select `QEMU HARDDISK Media` (\~103.08GB) from the list (on
            Big Sur and above use `Apple Inc. VirtIO Block Device`) and
            click **Erase**.
        -   Enter a `Name:` for the disk
        -   If you are installing macOS Mojave or later (Catalina, Big
            Sur, Monterey, Ventura and Sonoma), choose any of the APFS
            options as the filesystem. MacOS Extended may not work.
    -   Click **Erase**.
    -   Click **Done**.
    -   Close Disk Utility
-   From **macOS Utilities**
    -   Click **Reinstall macOS** and **Continue**
-   Complete the installation as you normally would.
    -   On the first reboot use cursor keys and enter key to select
        **macOS Installer**
    -   On the subsequent reboots use cursor keys and enter key to
        select the disk you named
-   Once you have finished installing macOS you will be presented with
    an the out-of-the-box first-start wizard to configure various
    options and set up your username and password
-   OPTIONAL: After you have concluded the out-of-the-box wizard, you
    may want to enable the TRIM feature that the computer industry
    created for SSD disks. This feature in our macOS installation will
    allow QuickEmu to compact (shrink) your macOS disk image whenever
    you delete files inside the Virtual Machine. Without this step your
    macOS disk image will only ever get larger and will not shrink even
    when you delete lots of data inside macOS.
    -   To enable TRIM, open the Terminal application and type the
        following command followed by pressing
        <kbd>enter</kbd> to tell macos to use the TRIM
        command on the hard disk when files are deleted:

``` shell
sudo trimforce enable
```

You will be prompted to enter your account's password to gain the
privilege needed. Once you've entered your password and pressed
<kbd>enter</kbd> the command will request confirmation
in the form of two questions that require you to type
<kbd>y</kbd> (for a "yes" response) followed by
<kbd>enter</kbd> to confirm.

If you press <kbd>enter</kbd> without first typing
<kbd>y</kbd> the system will consider that a negative
response as though you said "no":

``` plain
IMPORTANT NOTICE: This tool force-enables TRIM for all relevant attached devices, even though such devices may not have been validated for data integrity while using TRIM. Use of this tool to enable TRIM may result in unintended data loss or data corruption. It should not be used in a commercial operating environment or with important data. Before using this tool, you should back up all of your data and regularly back up data while TRIM is enabled. This tool is provided on an "as is" basis. APPLE MAKES NO WARRANTIES, EXPRESS OR IMPLIED, INCLUDING WITHOUT LIMITATION THE IMPLIED WARRANTIES OF NON-INFRINGEMENT, MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE, REGARDING THIS TOOL OR ITS USE ALONE OR IN COMBINATION WITH YOUR DEVICES, SYSTEMS, OR SERVICES. BY USING THIS TOOL TO ENABLE TRIM, YOU AGREE THAT, TO THE EXTENT PERMITTED BY APPLICABLE LAW, USE OF THE TOOL IS AT YOUR SOLE RISK AND THAT THE ENTIRE RISK AS TO SATISFACTORY QUALITY, PERFORMANCE, ACCURACY AND EFFORT IS WITH YOU.
Are you sure you with to proceed (y/N)?
```

And a second confirmation once you've confirmed the previous one:

``` plain
Your system will immediately reboot when this is complete.
Is this OK (y/N)?
```

As the last message states, your system will automatically reboot as
soon as the command completes.

The default macOS configuration looks like this:

``` shell
guest_os="macos"
img="macos-catalina/RecoveryImage.img"
disk_img="macos-catalina/disk.qcow2"
macos_release="catalina"
```

-   `guest_os="macos"` instructs Quickemu to optimise for macOS.
-   `macos_release="catalina"` instructs Quickemu to optimise for a
    particular macOS release.
    -   For example VirtIO Network and Memory Ballooning are available
        in Big Sur and newer, but not previous releases.
    -   And VirtIO Block Media (disks) are supported/stable in Catalina
        and newer.

There is further advice and information about macOS guests in the
project
[wiki](https://github.com/quickemu-project/quickemu/wiki/03-Create-macOS-virtual-machines#automatically-create-macos-guests).

## [Creating Windows guests](https://github.com/quickemu-project/quickemu/wiki/04-Create-Windows-virtual-machines) 🪟

`quickget` can download [**Windows
10**](https://www.microsoft.com/software-download/windows10) and
[**Windows 11**](https://www.microsoft.com/software-download/windows11)
automatically and create an optimised virtual machine configuration.
This configuration also includes the [VirtIO drivers for
Windows](https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/).

**Windows 8.1** is also supported but doesn't feature any automated
installation or driver optimisation.

`quickget` can also download [Windows 10
LTSC](https://www.microsoft.com/en-us/evalcenter/download-windows-10-enterprise)
and Windows Server
[2012-r2](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2012-r2),
[2016](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2016),
[2019](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019),
and
[2022](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2022).
No automated installation is supported for these releases.

``` shell
quickget windows 11
quickemu --vm windows-11.conf
```

-   Complete the installation as you normally would.
-   All relevant drivers and services should be installed automatically.
-   A local administrator user account is automatically created, with
    these credentials:
    -   Username: `Quickemu`
    -   Password: `quickemu`

Further information is available from the project
[wiki](https://github.com/quickemu-project/quickemu/wiki/04-Create-Windows-virtual-machines)

# AUTHORS

Written by Martin Wimpress.

# BUGS

Submit bug reports online at:
<https://github.com/quickemu-project/quickemu/issues>

# SEE ALSO

Full sources at: <https://github.com/quickemu-project/quickemu>

quickemu(1), quickemu_conf(1), quickgui(1)
