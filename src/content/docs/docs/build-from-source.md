---
title: Build from source
description: Build the full desktop, or a single component, with meson.
---

Today, running Singularity means building it. This page covers the full build
and building a single component on its own.

:::danger[Pre-release: install at your own risk]
Singularity is in active development. Building and installing it touches your
system and carries real risk: it has been tested on several machines, but there is
no guarantee it will not break something, or, worse, leave the device unable to
boot. Try it on a spare machine or a virtual machine, and back up anything you
care about first.

So far it has been tested only on Vanilla OS 2 Orchid, Vanilla OS 3 Reunion,
Debian Sid, and Ubuntu 26.04 (Resolute Raccoon). Other systems may not work.

On immutable systems, do not install into the system prefix. Use
`make deploy-host`, which deploys to `/opt/local`, instead.
:::

## The full build

The meta repo wires everything together as submodules:

```sh
git clone --recurse-submodules <meta-repo-url> singularity-desktop
cd singularity-desktop
make compile
```

`make install` installs to `/usr/local`, with an optional `/usr`.
`make deploy-host` deploys to `/opt/local` for container-based workflows.

## What you need

The build is GTK4 and Vala throughout, driven by meson. Beyond a Vala toolchain
and GTK4, the components pull in the libraries they each need, such as
GtkSourceView for the editors, VTE for the terminal, GStreamer for the media
apps, and `libpeas` for plugins. The `vetro` transpiler must be on your `PATH`,
since the build invokes it to turn `.vetro` files into GTK `.ui`. See
[vetro](/docs/vetro/).

## Build a single component

Each component builds on its own with meson, as long as `libsingularity` is
installed and discoverable via `pkg-config`:

```sh
meson setup build
meson compile -C build
```

If `pkg-config --exists singularity-1.0` fails, point it at the install prefix:

```sh
export PKG_CONFIG_PATH=/usr/local/lib64/pkgconfig:$PKG_CONFIG_PATH
```

See [Build an App](/docs/build-an-app/) for the app workflow, and
[Repositories](/docs/repositories/) for how the pieces fit together.
