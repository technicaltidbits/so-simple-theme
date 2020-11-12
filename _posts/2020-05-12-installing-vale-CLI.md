---
title: "Testing docs with Vale - Part 1: Installing the Vale CLI"
layout: post
read_time: true
words_per_minute: 200
tags: [testing, vale, docs-as-code, QA]
excerpt: In this tutorial, you'll learn how to install Vale, a style linter. In part one, you'll learn how to use a package manager to install Vale on your Mac or PC.
---

In this tutorial, you'll learn how to install Vale, a style linter. This tool allows you to lint your doc files. I've planned four parts for this series:

* Part 1: **Installing the Vale CLI**.\
  In this part, you'll learn how to use a package manager to install Vale on your Mac or PC.
* Part 2: **Configuring the Vale CLI**.\
  In this part, you'll learn how to configure the Vale CLI for your documentation needs. It focuses on the basic structure of an initialization file, which you'll need to use Vale.
* Part 3: **Linting files with Vale**.\
  In this part, you'll create an initialization file, customize it, and lint some Markdown files.
* Part 4: **Customizing Vale styles.**\
  In this last part, you'll learn how to create and customize your own styles.

By the time you finish the series, you'll have a basic understanding of how you can configure Vale to your liking and how to create and customize your own styles.

# How to install the Vale CLI

To install Vale on your computer, you'll need to use a package manager. Package managers allow you to install and update packages and libraries. Mac users will use [Homebrew](#for-mac-users); Windows users will use [Chocolatey](#for-windows-users).

## For Mac users

The best package manager for macOS is Homebrew. If you've already installed Homebrew, skip to step two. Otherwise, continue reading the instructions below.

### Step 1: Install Homebrew

To install Homebrew, enter this command into the terminal (feel free to copy and paste):

`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"`

To verify that you installed Homebrew, run the command `brew help`. If the installation was successful, the command prints the help documentation to the terminal.

### Step 2: Install Vale

From the terminal, run the command `brew install vale`. You'll see some output in the terminal as Homebrew installs Vale.

Verify that the vale command is now available by running `vale -v` from the command line. If the installation was successful, the command reports the latest, stable version of Vale.

## For Windows users

Windows users can install Vale using Chocolatey. If you've already installed Chocolatey, skip to step two. Otherwise, continue reading the instructions below.

### Step 1: Install Chocolatey

Follow [these](https://chocolatey.org/install) steps to install Chocolatey on your computer.

To verify that you installed Chocolatey, run the command `choco -?`. If the installation was successful, the command prints the help documentation to the terminal.

### Step 2: Install Vale

From the terminal, run the command `choco install vale`. You'll see some output in the terminal as Chocolatey installs Vale on your computer.

To verify that you installed Vale, run the command `vale -v` in the terminal. If the installation was successful, the command reports the latest, stable version of Vale.

## What's next

That's all you need to do to install the Vale CLI! Next, you'll learn how to configure and customize Vale for your documentation needs.