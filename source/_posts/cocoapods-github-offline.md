---
title: Fix github is offline when running cocoapods
date: 2018-03-19 11:29:21
tags:
---

I will write how to fix the error you meet when you are running cocoapods.
Cocoapods sometimes says that GitHub is offline even if you are connected to the internet.
The reason why it happens is that Github [removed support for weak cryptographic standards](https://blog.github.com/2018-02-23-weak-cryptographic-standards-removed/). That's why your connection is refused by Github.

In this post, I will show you how to fix this issue step by step.

<!-- more -->

## Homebrew and Commandline Tool

First, please make sure that you already installed `homebrew` and Xcode command line tools.

install homebrew

    /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

install Xcode command line tool

    xcode-select -install

## install RVM and Ruby (again)

Next upgrade ruby version, since default ruby version and default ssl version are ancient ones in Sierra, probably even in High Sierra.
Now we are going to use [RVM](https://rvm.io), which is ruby version management tool.

    \curl -sSL https://get.rvm.io | bash -s stable

Run this command, and it will install `rvm` under your `$HOME`. When it's done, now it's time to upgrade your ruby.

    rvm install 2.4

You can choose whatever version you like, now I selected ruby 2.4. Currently, 2.4 is the most stable latest version.
Let me explain a bit how it works. `rvm install` doesn't pollute your root environment. Instead, it creates kind of "sandbox" environment. It just installs the ruby in your $HOME/.rvm and you can uninstall it anytime without any side effects.

And in this step, thing is that when you install ruby, it also install the latest OpenSSL at the same time. That's the point.
The new openssl library will solve github ssl issue.

## install cocoapods again

Then, you have ruby 2.4 with new OpenSSL. Your ruby environment is totally clean and has no modules. So you have to install cocoapods again.

    gem install cocoapods

Great! We are all set!

You may want to install other modules, like fastlane. please do it. There are no worries.

    gem install fastlane

## update pod

You can upgrade your dependencies.

    pod repo update # if it fails, try again. It seems if fails several times.
    pod install
