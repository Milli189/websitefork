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
git clone --recurse-submodules https://github.com/singularityos-lab/singularity-desktop.git singularity-desktop
cd singularity-desktop
make compile
```

`make install` installs to `/usr/local`, with an optional `/usr`.
`make deploy-host` deploys to `/opt/local` for container-based workflows.

## What you need

The build is GTK4 and Vala throughout, driven by meson, and it pulls in a fair
number of libraries. The shell uses GTK4, gtk4-layer-shell, VTE, libpeas,
PulseAudio, NetworkManager, UPower, polkit, libsoup, and Tracker, plus the Wayland
and X libraries; the apps add GtkSourceView, GStreamer, GNOME Online Accounts,
libsecret, poppler, and WebKitGTK; and the labwc compositor brings the usual
wlroots stack. You also need the build tools (meson, ninja, Vala, git, gettext,
pkg-config, gobject-introspection, wayland-scanner, scdoc) and the `vetro`
transpiler on your `PATH`, since the build invokes it to turn `.vetro` files into
GTK `.ui`. See [vetro](/docs/vetro/).

:::caution[These commands are generic]
The lists below are a starting point, not a guarantee. Package names and
availability change between distributions and releases, so check each one against
your own distro's repositories and adjust before running them.
:::

On Ubuntu or Debian:

```sh
sudo apt install \
  build-essential meson ninja-build valac git gettext pkg-config scdoc \
  gobject-introspection wayland-protocols \
  libgtk-4-dev libglib2.0-dev libgee-0.8-dev libjson-glib-dev libpeas-2-dev \
  libgtk4-layer-shell-dev libgtksourceview-5-dev libvte-2.91-gtk4-dev \
  libgnome-desktop-4-dev libgoa-1.0-dev libgoa-backend-1.0-dev \
  libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev \
  libpulse-dev libnm-dev libupower-glib-dev \
  libpolkit-agent-1-dev libpolkit-gobject-1-dev libsoup-3.0-dev \
  libtracker-sparql-3.0-dev libsecret-1-dev libgudev-1.0-dev librsvg2-dev \
  libpoppler-glib-dev libwebkitgtk-6.0-dev libxml2-dev \
  libpango1.0-dev libcairo2-dev libpixman-1-dev libdrm-dev libinput-dev \
  libxkbcommon-dev libwayland-dev libxcb1-dev libxcb-ewmh-dev libxcb-icccm4-dev \
  libatspi2.0-dev libdbusmenu-glib-dev libsystemd-dev libpng-dev \
  libsodium-dev libgcrypt20-dev
```

On Arch:

```sh
sudo pacman -S --needed \
  base-devel meson ninja vala git gettext scdoc \
  gobject-introspection wayland-protocols \
  gtk4 glib2 libgee json-glib libpeas2 gtk4-layer-shell gtksourceview5 vte4 \
  gnome-desktop gnome-online-accounts gstreamer gst-plugins-base \
  libpulse networkmanager upower polkit libsoup3 tinysparql libsecret \
  libgudev librsvg poppler-glib webkitgtk-6.0 libxml2 pango cairo pixman \
  libdrm libinput libxkbcommon wayland libxcb xcb-util-wm at-spi2-core \
  libdbusmenu-glib systemd libpng libsodium libgcrypt wlroots
```

On Fedora:

```sh
sudo dnf install \
  @development-tools meson ninja-build vala git gettext pkgconf-pkg-config scdoc \
  gobject-introspection-devel wayland-protocols-devel \
  gtk4-devel glib2-devel libgee-devel json-glib-devel libpeas-devel \
  gtk4-layer-shell-devel gtksourceview5-devel vte291-gtk4-devel \
  gnome-desktop4-devel gnome-online-accounts-devel \
  gstreamer1-devel gstreamer1-plugins-base-devel \
  pulseaudio-libs-devel NetworkManager-libnm-devel upower-devel \
  polkit-devel libsoup3-devel tinysparql-devel libsecret-devel libgudev-devel \
  librsvg2-devel poppler-glib-devel webkitgtk6.0-devel libxml2-devel \
  pango-devel cairo-devel pixman-devel libdrm-devel libinput-devel \
  libxkbcommon-devel wayland-devel libxcb-devel xcb-util-wm-devel \
  at-spi2-core-devel libdbusmenu-devel systemd-devel libpng-devel \
  libsodium-devel libgcrypt-devel wlroots-devel
```

The `vetro` transpiler is a separate program, kept in
[its own repository](https://github.com/singularityos-lab/vetro); install it and
make sure it is on your `PATH` before building.

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
