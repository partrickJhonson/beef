## Introduction
The following installation instructions are suitable for **Linux** based operating systems.

In theory, BeEF should work on any operating system which can run Ruby 2.5+ and NodeJS. However, only MacOS and Linux are officially supported.

You will not find MacOS installation instructions in this guide. They are currently high on the list of wiki tasks to be completed.

#### Table of Contents
* [Prerequisites](#prerequisites)
* [Source](#source)
* [Installation](#installation)
* [BeEF on Ubuntu](#beef-on-ubuntu)
* [Start BeEF](#start-beef)
* [Testing](#testing)
* [Updating](#updating)

## Prerequisites

BeEF requires Ruby 2.5 (or newer). Refer to your operating system documentation
for instructions to install the latest stable version of Ruby and Ruby Developer Tools.

```bash
Debian based systems
$ sudo apt-get install ruby ruby-dev

RedHat / Fedora
$ sudo yum install ruby ruby-devel
```

If your operating system package manager does not support Ruby version 2.5 (or newer),
you can add the brightbox ppa repository for the latest version of Ruby:

```bash
$ sudo apt-add-repository -y ppa:brightbox/ruby-ng
```

Alternatively, consider using a Ruby environment manager such as
[rbenv](https://github.com/rbenv/rbenv) or
[rvm](https://rvm.io/rvm/install).

These are command line tools that allow for simple management of different Ruby environments.

### Bundler

Bundler is essential for tracking and installing the correct gems in ruby projects.
When installing, you may get the error:
```bash
$ line 208: bundle: command not found 
```
This just means you do not have bundler installed, to fix this simply run:
```bash
$ gem install bundler
```
## BeEF on Ubuntu

It's highly recommended that you use a Ruby Environment Manager when installing BeEF on Ubuntu, due to restricted permissions. Please note that you do not need to install Ruby as per the above instructions, if using Ruby Environment Manager.

In order to install BeEF and RVM you will need to install Git and Curl first, as they do not come out of the box with Ubuntu.

```bash
$ sudo apt-get install git
$ sudo apt-get install curl
```

To install RVM, firstly go to https://rvm.io/rvm/install and install the GPG keys.
Then install RVM, without dependencies:

```bash
$ \curl -sSL https://get.rvm.io | bash -s -- --autolibs=install-packages 
```
Now install those dependencies as root while in the applications users $HOME directory:

```bash
$ sudo .rvm/bin/rvm requirements 
```

Now that the dependencies are installed we need to install the stable releases of both RVM and Ruby. As the application user enter:

```bash
$ \curl -sSL https://get.rvm.io | bash -s stable --ruby
```
BeEF requires Ruby 2.5.x. Before navigating to the beef directory run:

```bash
$ rvm install "ruby-2.5.3"
```

Then simply reload your shell!

You can verify your installation of RVM and Ruby by running:

```bash
$ rvm -v
$ ruby -v
```

After following the above steps, simply clone the repository and install BeEF as per below.
## Source

Obtain application source code either by downloading the latest archive:

```bash
$ wget https://github.com/beefproject/beef/archive/master.zip
```

Or cloning the Git repository from Github:

```bash
$ git clone https://github.com/beefproject/beef
```


## Installation

Once a suitable version of Ruby is installed, run the
[install script](https://github.com/beefproject/beef/blob/master/install) in the BeEF directory:

```bash
$ ./install
```

This script installs the required operating system packages and all the
prerequisite Ruby gems.

Upon successful installation, be sure to read the
[Configuration](https://github.com/beefproject/beef/wiki/Configuration)
page on the wiki for important details on configuring and securing BeEF.


## Start BeEF

To start BeEF, first change the username and password config.yaml and then simply run:

```bash
  $ ./beef
```
## Testing

If you want to install the test pre-requisites just run:

``` bash
$ bundle install --with test
```

This will install the pre-requisite gem's for tests.

If you want to run the test suit run:

```bash
$ bundle exec rake
```
## Updating

Due to the fast-paced nature of web browser development and webappsec landscape,
it's best to regularly update BeEF to the latest version.

If you're using BeEF from the GitHub repository, updating is as simple as:

```bash
$ git pull
```

***
[[Previous|Architecture]] | [[Next|Configuration]]