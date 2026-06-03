---
title: First boot
description: The greeter, logging in, and choosing your session.
---

When you start your machine, the first thing you meet is the greeter.

## The greeter

The greeter lists the users on the system and lets you sign in. It is built on
the same framework as the rest of the desktop, so it already looks like
Singularity before you have logged in once.

Each user gets their own look on the login screen. The greeter reads your accent
color and your wallpaper from the system account service, so the background you
chose inside the desktop shows up, gently blurred, when you log in. Your avatar
appears too, taken from your account picture.

## Choosing a session

If more than one desktop session is installed, the greeter lets you choose which
one to start. It finds sessions the standard way, by scanning the usual system
locations for installed session files, so anything installed correctly shows up
in the list. Pick the Singularity session and sign in.

## After login

The session launcher starts the compositor, then the shell, and keeps the
desktop alive across restarts. The first thing you will see is the
[desktop](/docs/desktop-tour/): a panel at the top and a dock at the bottom.
