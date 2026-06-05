---
title: Install
description: The ways to run Singularity today.
---

There are two ways to get Singularity, and only one of them is ready right now.

:::danger[Pre-release: install at your own risk]
Singularity is in active development. Building and installing it touches your
system and carries real risk: it has been tested on several machines, but there is
no guarantee it will not break something, or, worse, leave the device unable to
boot. Try it on a spare machine or a virtual machine, and back up anything you
care about first.

So far it has been tested only on Vanilla OS 2 Orchid, Vanilla OS 3 Reunion,
Debian Sid, and Ubuntu 26.04 (Resolute Raccoon). Other systems may not work.

On immutable systems, do not install into the system prefix. `make install`
already deploys to `/opt/local`, the persistent writable prefix.
:::

## The OS image

Singularity OS, the full operating system, is still being built. When it is
ready, an installable image will be the simplest way to run the whole thing.
For now, see [Singularity OS](/docs/singularity-os/) for what it is and where it
is going.

## Build from source

Today, the way to run the desktop is to build it. The meta repository wires
every component together as submodules and builds them with a single command:

```sh
git clone --recurse-submodules https://github.com/singularityos-lab/singularity-desktop.git singularity-desktop
cd singularity-desktop
make compile
make install
```

`make install` does the full install to `/opt/local` (binaries, bundled
libraries, portal and systemd wiring, icon theme, and session entry), and
self-elevates when needed. `make deploy-host` is a deprecated alias kept for
compatibility; it now just runs `make install`.

Once installed, the session shows up in your display manager. Log in through the
[greeter](/docs/first-boot/) and pick the Singularity session.

The full build options, dependencies, and single-component builds are covered in
[Build from source](/docs/build-from-source/).
