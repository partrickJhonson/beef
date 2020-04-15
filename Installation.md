# Introduction <!-- omit in toc -->
The following installation instructions are suitable for **Linux** based operating systems.

In theory, BeEF should work on any operating system which can run Ruby 2.5+ and NodeJS. However, only MacOS and Linux are officially supported.

You will not find MacOS installation instructions in this guide. They are currently high on the list of wiki tasks to be completed.

#### Table of Contents <!-- omit in toc -->
- [Prerequisites](#prerequisites)
  - [Ruby](#ruby)
  - [Bundler](#bundler)
  - [Source](#source)
  - [Docker](#docker)
- [Ubuntu Installation](#ubuntu-installation)
  - [Installation](#installation)
  - [Start BeEF](#start-beef)
  - [Testing](#testing)
  - [Updating](#updating)
- [Docker Setup](#docker-setup)
  - [Setting Your Credentials](#setting-your-credentials)
  - [Building Your Image & Container](#building-your-image--container)
  - [Troubleshooting](#troubleshooting)
  - [Connecting to BeEF](#connecting-to-beef)
  - [Updating Your Image](#updating-your-image)
  

## Prerequisites

### Ruby

**Pre-requisite for:** [Ubuntu](#ubuntu-installation)

BeEF requires Ruby 2.5 (or newer). Refer to your operating system documentation
for instructions to install the latest stable version of Ruby and Ruby Developer Tools.

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

**Pre-requisite for:** [Ubuntu](#ubuntu-installation)

Bundler is essential for tracking and installing the correct gems in ruby projects.
When installing, you may get the error:

```bash
line 208: bundle: command not found
```

This just means you do not have bundler installed, to fix this simply run:

```bash
$ gem install bundler
```
### Source

**Pre-requisite for:** [Ubuntu](#ubuntu-installation), [Docker](#docker-setup)

Obtain application source code either by downloading the latest archive:

```bash
$ wget https://github.com/beefproject/beef/archive/master.zip
```

Or cloning the Git repository from Github:

```bash
$ git clone https://github.com/beefproject/beef
```

### Docker

**Pre-requisite for:** [Docker](#docker-setup)

Please follow the setup instructions over on the [Docker Installation Guide](https://docs.docker.com/get-docker/).

## Ubuntu Installation

**Pre-requisites:** [Source Code](#source), [Ruby](#ruby), [Bundler](#bundler)

It's highly recommended that you use a Ruby Environment Manager when installing BeEF on Ubuntu, due to restricted permissions. Please note that you do not need to install Ruby as per the above instructions, if using Ruby Environment Manager.

In order to install BeEF and RVM you will need to install Git and Curl first, as they do not come out of the box with Ubuntu.

```bash
$ sudo apt-get install git
$ sudo apt-get install curl
```

To install RVM, firstly go to <https://rvm.io/rvm/install> and install the GPG keys.
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

### Installation

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


### Start BeEF

To start BeEF, first change the username and password config.yaml and then simply run:

```bash
  $ ./beef
```

### Testing

If you want to install the test pre-requisites just run:

``` bash
$ bundle install --with test
```

This will install the pre-requisite gem's for tests.

If you want to run the test suit run:

```bash
$ bundle exec rake
```

### Updating

Due to the fast-paced nature of web browser development and webappsec landscape,
it's best to regularly update BeEF to the latest version.

If you're using BeEF from the GitHub repository, updating is as simple as:

```bash
$ git pull
```

## Docker Setup

**Pre-requisites:** [Source Code](#source), [Docker](#docker-setup)

Running BeEF through Docker alleviates any host setup pains, making the installation process as simple as executing a few commands.

### Setting Your Credentials

It is essential that you set your credentials BEFORE building your Docker image. BeEF by default has it's credentials set to `beef:beef`, but does not allow authentication with default credentials. Consequently if you build an image without changing the credentials you will not be able to authenticate your container's BeEF instance.

With your preferred text editor open the `config.yaml` file found in the BeEF root folder:

```yaml
  ...SNIP...
    credentials:
      user: '<YOUR_USERNAME>'
      passwd: '<YOUR_PASSWORD>'
  ...SNIP...
```

### Building Your Image & Container


To build your image:

```bash
  $ docker build -t beef .
```

To run your container:

```bash
  # If you'd prefer the container to run backgrounded/detached just add the -d tag to the command below
  $ docker run -p 3000:3000 -p 6789:6789 -p 61985:61985 -p 61986:61986 --name beef beef
```

To run your container without executing the normal start-up, and instead spawn a shell on the box:

```bash
  $ docker run -p 3000:3000 -p 6789:6789 -p 61985:61985 -p 61986:61986 --name beef --entrypoint=/bin/bash -it beef
```

To get a shell on the container:

```bash
  $ docker exec -it beef /bin/bash # You can replace /bin/bash to run an arbitrary command
```

To stop your container:

```bash
  $ docker stop beef
```


To start your container:

```bash
  $ docker start beef
```

### Troubleshooting

If you run into this error:

```bash
  You must use Bundler 2 or greater with this lockfile.
  The command '/bin/sh -c apk add --no-cache git curl libcurl curl-dev ruby-dev libffi-dev make g++ gcc musl-dev zlib-dev sqlite-dev &&   bundle install --system --clean --no-cache \
  --gemfile=/beef/Gemfile $BUNDLER_ARGS &&   rm -rf /usr/local/bundle/cache' returned a non-zero code: 20
```

Delete the Gemfile.lock from your BeEF directory and try again.

### Connecting to BeEF

The IP address the Docker container runs on may vary from machine to machine. The easiest way to check is to run:

```bash
  $ docker exec -it beef ifconfig eth0
```

Here you will need to look for the IP address beside `inet`. For example, the address I would need to navigate to in the example below is `172.17.0.2`:

```bash    
  eth0    inet addr:172.17.0.2  Bcast:172.17.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4466 (4.3 KiB)  TX bytes:1770 (1.7 KiB)
```

Once you've identifed your containers IP address navigate to `http://IP_ADDRESS:3000/ui/authentication`


### Updating Your Image

Every time you pull down the latest source code (`git pull origin master`), or update using `/beef/update-beef` you will need to rebuild your image as described above.

***
[[Introducing BeEF|Introducing BeEF]] | [[Configuration|Configuration]]