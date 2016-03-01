# BTFS (bittorrent filesystem)

## What is this?

With BTFS, you can mount any **.torrent** file or **magnet link** and then use it as any read-only directory in your file tree. The contents of the files will be downloaded on-demand as they are read by applications. Tools like **ls**, **cat** and **cp** works as expected. Applications like **vlc** and **mplayer** can also work without changes.

## Example usage

    $ mkdir mnt
    $ btfs video.torrent mnt
    $ cd mnt
    $ vlc video.mp4

To unmount and shutdown:

    $ fusermount -u mnt

## Installing on Debian/Ubuntu

    # apt-get install btfs

## Installing on Arch Linux

    # pacman -S btfs

## Installing on Gentoo

    # emerge -av btfs

## Installing on macOS

Use [`brew`](https://brew.sh) to install on macOS.

    $ brew install btfs

## Building on OS X

Use `brew` to get the dependencies and clone the project.

    $ brew install Caskroom/cask/osxfuse libtorrent-rasterbar autoconf automake pkg-config
    $ git clone https://github.com/johang/btfs.git btfs
    $ cd btfs

Open the file `configure.ac` and replace `fuse >= 2.8.0` with `fuse >= 2.7.3` (**Only if you have the latest osxfuse version!**, see why on [pull request #5](https://github.com/johang/btfs/pull/5)). Then:

    $ autoreconf -i
    $ ./configure
    $ make
    $ sudo make install

## Installing on OS X

BTFS is known to work on Apple's OS X. See [pull request #5](https://github.com/johang/btfs/pull/5) for more information.

## Dependencies (on Linux)

* fuse ("fuse" in Ubuntu 16.04)
* libtorrent ("libtorrent-rasterbar8" in Ubuntu 16.04)
* libcurl ("libcurl3" in Ubuntu 16.04)

## Building from git on a recent Debian/Ubuntu

    $ sudo apt-get install autoconf automake libfuse-dev libtorrent-rasterbar-dev libcurl4-openssl-dev g++
    $ git clone https://github.com/johang/btfs.git btfs
    $ cd btfs
    $ autoreconf -i
    $ ./configure
    $ make

And optionally, if you want to install it:

    $ make install

## Building on macOS

Use [`brew`](https://brew.sh) to get the dependencies.

    $ brew install Caskroom/cask/osxfuse libtorrent-rasterbar autoconf automake pkg-config
    $ git clone https://github.com/johang/btfs.git btfs
    $ cd btfs
    $ autoreconf -i
    $ ./configure
    $ make

And optionally, if you want to install it:

    $ make install
