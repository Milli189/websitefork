---
title: Store
description: Find and install apps from Flathub.
---

Store is where you find more apps for Singularity. It browses Flathub and
installs apps as Flatpaks, so it sits on top of the same packaging the rest of
the Linux desktop uses.

## Browsing

The sidebar organizes the catalog into Featured (editor's picks and new and
noteworthy), Popular, Recently updated, and Categories covering the usual
ground from Development to Games to Office. There is also a search box that
queries Flathub directly. An Installed page lists the Flatpaks already on your
machine, and an Updates page collects what has a new version, with an Update all
button.

## App pages

Opening an app shows its icon, developer, and summary, a carousel of
screenshots, the full description, and the permissions it asks for, such as
network, audio, or file access. Where Flathub has them, star ratings and user
reviews appear too.

## Installing

The Get button installs the app with Flatpak and shows the live install log as
it runs, so you can watch progress and see any errors. Updating and removing work
the same way, from the app page or the Installed and Updates lists.

:::caution[Still in development]
Store is an early storefront. It needs Flatpak set up with the Flathub remote to
work, and it leans on the `flatpak` command under the hood. Expect rough edges
around error handling and offline behavior.
:::
