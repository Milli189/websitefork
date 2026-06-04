---
title: Troubleshooting
description: Common questions and how to get unstuck.
---

This is early software. When something goes wrong, here are the first things to
check.

## The session does not start

Make sure Singularity is installed where your display manager looks for
sessions, and that you picked the Singularity session in the
[greeter](/docs/first-boot/). The greeter only lists sessions it can find in the
standard system locations, so a session installed somewhere unusual will not
appear.

## The shell, dock, and panels open as separate windows

If the desktop components appear as ordinary floating windows instead of being
anchored to the screen edges, Singularity was started outside its compositor.
The shell, dock, and panels are Wayland layer-shell surfaces that rely on labwc
to place them; launched on their own, or inside another compositor, they fall
back to regular toplevel windows. Start the desktop through the Singularity
session from the [greeter](/docs/first-boot/), or from a TTY run
`singularity-labwc-session`, which brings up labwc and the shell together.

## The desktop has no icons

Singularity currently draws its icons from the Adwaita icon theme. If buttons
and apps show up without any icons, that icon pack is missing. Install your
distribution's Adwaita icon theme (commonly packaged as `adwaita-icon-theme`)
and restart the session.

## The shell crashed or looks wrong

The session keeps the shell alive and restarts it if it stops, so a glitch
usually clears on its own. You can also restart the shell yourself from
[Spotlight](/docs/spotlight/): open it and run `r`.

## My accent color did not apply

The accent is applied across the desktop and the window borders together. If a
single app did not follow, it may not be reading the shared settings; the
first-party apps all do. Setting the accent again from
[Appearance](/docs/appearance/) reapplies it everywhere.

## A shortcut does not work

Some shortcuts are handled by the shell and some by the compositor. If a custom
shortcut does not fire, check it in the keyboard settings; custom shortcuts are
pushed to the compositor as well, and a conflicting binding can shadow them.

## Notifications are not showing

Check whether Do Not Disturb is on. It suppresses the popups while still keeping
everything in the [notification center](/docs/notifications/).

## Getting help

The project talks in the open. The [news](/news/) covers what is landing, and
the repositories are where to file what you find.
