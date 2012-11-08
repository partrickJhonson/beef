## Installation on Windows

***

## Installation on Linux

### Debian / Ubuntu

**Install dependencies**

```bash
    $ sudo apt-get update 
    $ sudo apt-get install curl git ruby build-essential libsqlite3-ruby libsqlite3-dev build-essential libsqlite3-ruby libsqlite3-dev
    $ sudo curl https://raw.github.com/wayneeseguin/rvm/master/binscripts/rvm-installer | bash -s stable
    $ sudo echo [[ -s "$HOME/.rvm/scripts/rvm" ]] && . "$HOME/.rvm/scripts/rvm" # Load RVM function' >> ~/.bash_profile 
    $ sudo source ~/.bash_profile
    $ rvm pkg install zlib $ rvm install 1.9.3
    $ rvm use 1.9.3
```

**Download BeEF**

```bash
    $ git clone git://github.com/beefproject/beef.git
```

**Install gems and launch**

```bash
    $ cd beef
    $ sudo gem install bundler
    $ sudo bundle install
    $ ruby beef
```

### Red Hat / Fedora

**Install dependencies**

```bash
    $ sudo yum install -y git make gcc openssl-devel gcc-c++ patch readline readline-devel zlib zlib-devel libyaml-devel libffi-devel bzip2 autoconf automake libtool bison iconv-devel sqlite-devel
    $ wget https://raw.github.com/wayneeseguin/rvm/master/binscripts/rvm-installer
    $ bash ./rvm-installer
    $ source ~/.rvm/scripts/rvm
    $ rvm pkg install openssl
    $ rvm install 1.9.2 --with-openssl-dir=$rvm_path/usr
    $ source ~/.rvm/scripts/rvm
    $ rvm use 1.9.2 --default
    $ gem install bundler
```

**Download BeEF**

```bash
    $ git clone git://github.com/beefproject/beef.git
```

**Install Gems and use it**

```bash
    $ cd beef
    $ bundle
    $ source ~/.bash_profile
    $ cd beef
    $ ./beef
```

### BackTrack

[[Look the dedicated page|BeEF-and-Backtrack-5]]

***

## Installation on MAC OS

**Install RVM and Ruby 1.9.3:**

```bash
    $ bash -s stable < <(curl -s https://raw.github.com/wayneeseguin/rvm/master/binscripts/rvm-installer) source ~/.bash_profile
    $ rvm install 1.9.3-p0 --with-gcc=clang
    $ rvm use 1.9.3
```

**Download BeEF**

You can download the [zip](https://github.com/beefproject/beef/zipball/master) or clone the git repository :

```bash
    $ git clone https://github.com/beefproject/beef.git
```

**Install Gems**

```bash
    $ bundle install
```

[[See detailed instruction on MAC OS X installation|MAC-OSX-installation-using-RVM]]

***
[Previous](wiki/Architecture] | [Next](wiki/Configuration)