# AQEMU

AQEMU is a graphical frontend for QEMU-based virtual machines. You can run it on Linux, FreeBSD, and **OpenBSD**.

## Screenshot

![ScreenShot](https://i.imgur.com/PkvFUEk.png)

## Dependencies

- meson
- libvncserver 
- qt5
    - Qt5Core
    - Qt5Widgets 
    - Qt5Network
    - Qt5Test
    - Qt5PrintSupport
    - Qt5DBus

## Installation

Example of how to build using meson/ninja:

```bash
$ meson builddir
$ cd builddir
$ ninja
$ ./aqemu
```

## OpenBSD

The original AQEMU by default doesn't compile under OpenBSD. Only this fork
is capable. For more info, see the note section.

### Compile and install under OpenBSD

First, install the needed dependencies,

```bash
$ doas pkg_add meson libvncserver qt5
```

Then follow the installation instruction stated above.

### OpenBSD troubleshooting

Since [OpenBSD Qt port stores the libs in a different directory](https://openports.pl/path/x11/qt5/qtbase),
in case the last stage of linking fails, open the `builddir/build.ninja` file
and make sure the `-L /usr/local/lib/qt5` flag exists before `-lQt5Core`.
If doesn't simply add and run `ninja` once again.

## Note about this fork

Unfortunately, as the [original project](https://github.com/tobimensch/aqemu)
is abandoned, I have to maintain this fork by myself. I'm neither a C++ nor
Qt developer. Originally, I wanted to run a QEMU client on OpenBSD and ended up porting AQEMU to OpenBSD. 

Any collaboration and patches are highly appreciated and always welcomed.
