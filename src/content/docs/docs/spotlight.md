---
title: Spotlight
description: Launch apps and run commands from one box.
---

Spotlight is the box that opens in the center of the screen for launching apps
and running commands. Press Super and Tab to open it, or Shift, Alt and F2.

## Apps or commands

The box does two things, and it tells you which one it is on. While it is empty
or you are typing a name, it is in search mode, with a lens icon, and it matches
your apps by name, command, and id, with the closest matches first. It shows up
to six suggestions; pick one with the arrow keys and Enter, or click it. The
placeholder reads "Search apps or run a command…".

Type something that is not an app and it becomes a command. Press Enter and
Spotlight runs it in your terminal, leaving the terminal open afterward so you
can see the output.

## Built-in commands

A few short commands are built in. The hint bar along the bottom reminds you of
them:

- `r` restarts the shell.

With developer mode turned on, two more appear, and the hint bar grows to list
them: `c` restarts the compositor, and `n` opens a nested test session.

## History

Spotlight remembers the commands you run, up to the last fifty, in your data
folder. Walk back through them with the Up and Down arrows so the things you do
often are quick to repeat. Press Escape to close the box.

## Deeper search in the overview

Spotlight is deliberately focused on apps and commands. The richer search lives
in the overview, which you open with Super and Space. There, the same search box
also finds your files through the system index, evaluates a math expression and
copies the answer to the clipboard when you pick it, and runs any custom search
providers you add. You can write your own: see
[Search providers](/docs/search-providers/).
