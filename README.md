# Pacman for Android

Archlinux pacman package manager ported to Android.

This project ported pacman to Android and tries to package ~~some useful packages~~(To be honest, some packages used by @kxxt) for Android.

This project is still in development, and it's not ready for use. **EVERYTHING IS SUBJECT TO CHANGE!!**

For me, one goal of this project is to maintain a useable docker package for Android
(Well, the termux project already maintains a docker package in their root-repo, but
[it is broken for now](https://gist.github.com/FreddieOliveira/efe850df7ff3951cb62d74bd770dce27?permalink_comment_id=4660318#gistcomment-4660318)).
To run docker, you need to build a custom kernel, see
[this guide](https://gist.github.com/FreddieOliveira/efe850df7ff3951cb62d74bd770dce27) for more details.

## Project Overview

- We use glibc instead of bionic libc.
- The prefix is `/data/usr`.
- Sysconfdir is `/data/etc`.
- Local state dir is `/data/var`. 
- `/data/opt`, but no `/data/run`, we use `/data/var/run` instead.
- The intended USER is `shell`, whose home dir is `/data/home/shell`.
- tmp dir is `/data/local/tmp`.
- No systemd support(yet).
- Some software might hardcode paths like `/usr/bin`, `/usr/lib`, `/usr/share`, etc. So some packages might not work properly. Please file an issue if you find one.
- Almost all packages are built on device. We usually don't cross-compile packages.
- For now I haven't decided the best way to deal with those annoying selinux policies on Android.
    - Some packages might not work properly because of selinux policies. Set selinux to permissive mode if you encounter any problem. (`setenforce 0`)
- For now I haven't decided the best way to deal with SYSVIPC on Android.
    - Some packages(e.g. fakeroot) provides a configure option to use other IPC mechanisms. We will use that option if possible.
    - Otherwise, nothing is done(yet) and you need a custom kernel with SYSVIPC enabled to use those packages.

## Platform Support Status

Android 13 is the only supported platform for now. Other platforms may work, but I didn't test them.

Architecture support status:

- aarch64: Supported
- armv7, armhf: Not supported
- x86_64: Why bothering using the poweruser-hostile Android if you are on x86_64?
- riscv64: Are you serious?

## How to use

TBA

