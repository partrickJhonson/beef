The following installation instructions are suitable for **Linux and Mac OSX** operating systems.

In theory, BeEF should work on any operating system which can run Ruby 2.4+ and nodejs. However, only MacOS and Linux are officially supported.

### Prerequisites

BeEF requires Ruby 2.4 (or newer). Refer to your operating system documentation
for instructions to install the latest stable version of Ruby and Ruby-dev.

```bash
# Debian based systems
sudo apt-get install ruby ruby-dev

# RedHat / Fedora
sudo yum install ruby ruby-devel
```

If your operating system package manager does not support Ruby version 2.4 (or newer),
you can add the brightbox ppa repository for the latest version of Ruby:

```bash
$ sudo apt-add-repository -y ppa:brightbox/ruby-ng
```

Alternatively, consider using a Ruby environment manager such as
[rbenv](https://github.com/rbenv/rbenv) or
[rvm](https://rvm.io/rvm/install)
to manager your Ruby versions.



### Source

Obtain application source code either by downloading the latest archive:

```bash
$ wget https://github.com/beefproject/beef/archive/master.zip
```

Or cloning the Git repository from Github:

```bash
$ git clone https://github.com/beefproject/beef
```


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

To start BeEF, simply run:

```bash
  $ ./beef
```

### Updating

Due to the fast-paced nature of web browser development and webappsec landscape,
it's best to regularly update BeEF to the latest version.

If you're using BeEF from the GitHub repository, updating is as simple as:

```bash
$ git pull
```

***
[[Previous|Architecture]] | [[Next|Configuration]]