# XYZ Maps CLI

We think developers deserve an easy to use, convenient and streamlined experience to work with XYZ Maps APIs. That’s why we’ve built the XYZ Maps CLI. XYZ Maps CLI is a Node.js command line interface which works not only with XYZ Maps, but eventually, with any XYZ API. Right now, it allows you to interact with XYZ Maps to create and manage your projects and easily upload and manage your datasets.

> #### XYZ Maps CLI on GitHub
>
>[XYZ Maps CLI is Open Source](https://github.com/xyzmaps/xyz-cli), where developers like yourself can contribute new functionality and features.

In this section, we'll quickly introduce you to the XYZ Maps CLI, how to install it and how to make the
most of it while working on your project. 

## Introduction

As mentioned before, the XYZ Maps CLI was built to make your life as a developer working with XYZ APIs
easier. It allows you to quickly try out new APIs to see how they behave before you get on to your
keyboard to actually develop an application. It can also be used to easily script common, repetitive
tasks or help in testing application logic or data.

## Quick Start

XYZ Maps CLI is built on Node.js, a cross-platform efficient language to write even complex, local applications.

### Install Node.js and npm

To use the new XYZ Maps CLI, you should have npm installed. The best way is to go to
[nodejs.org](https://nodejs.org/en/download/) and install the appropriate package for your
system (both 8.x LTS and 10.x Current should work).

#### Windows

Download the package and install it normally.

Alternatively, if you use a [package manager](https://nodejs.org/en/download/package-manager/#windows) like [Chocolatey](https://chocolatey.org/)
you just need an administrative cmd.exe/powershell.exe and run

    choco install -y nodejs

#### macOS

Similarly on macOS you can just download and install the `.pkg` package file.

You can also use your favorite [package manager](https://nodejs.org/en/download/package-manager/#macos), like homebrew:

    brew install node

#### Linux (Ubuntu, Fedora, Gentoo etc)

Follow the instructions at the [Node.js Package Manager](https://nodejs.org/en/download/package-manager/) site, find your dist and install the packages.

For Linux it's best to use [NVM](https://github.com/nvm-sh/nvm)
:

    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
    nvm install --lts

To be on the safe side you might want to install the optional `build-essentials` package as you might come across
native packages eventually and it's good to have the right tools around.

#### Check that it works

After installing, check in the command-line if `npm` is available. Depending on how you installed it you might need to close and reopen your terminal or command-line prompt.

    $ npm -v
    9.x.x

### Install XYZ Maps CLI

When you are sure your system has `node` and `npm` installed you can go ahead and install the latest
version of XYZ Maps CLI with following command:

    npm install -g xyzmaps-cli

> #### Note: Administrative permissions
>
> Depending on your system, you might need elevated system permissions to install **globally** with `-g`,
    which essentially means you can call the `here` command from anywhere.
>
> To elevate you permissions, either start an **Admin Command Prompt** or **Admin PowerShell** on Windows,
    or use `sudo` on Linux or macOS.

