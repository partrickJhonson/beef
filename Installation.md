## Installation on Windows

**Install dependencies**

* Download and Install: http://rubyinstaller.org/
* (Including the Development Kit, for more info see here: https://github.com/oneclick/rubyinstaller/wiki/Development-Kit)
* Download and Extract into your Ruby BIN folder: http://www.sqlite.org/sqlitedll-3_7_0_1.zip
* Add your Ruby BIN folder to your system PATH variable.
* Open a command Prompt and browse to where you extracted the Development Kit, run:
```
ruby dk.rb init
ruby dk.rb install
```
* Follow the steps described here: https://github.com/hiranpeiris/therubyracer_for_windows
This is needed because the admin UI is using the Uglifier gem, which needs a JavaScript environment. This is quite painful to install in Windows, so that link provides pre-compiled DLLs for the v8 engine and 2 required gems.
* Browse to where you extracted BeEF and run:
```
gem install bundler
```
* At this stage you should have the following gems installed:
```
bundler (1.5.1)
ref (1.0.5)
therubyracer (0.11.0beta1 x86-mingw32)
```
* You're now ready for the last step. After that, you can start BeEF.
```
bundle install
```


***

## Installation on Linux

Note, in any place listing RVM installation instructions you can replcae them with this two steps:

1. get ruby - assuming you do not want RVM and know a way to get ruby
2. run: `gem install bundler`


### Debian / Ubuntu

**Install dependencies**

```bash
    sudo apt-get update
    sudo apt-get install curl git
    curl -sSL https://raw.githubusercontent.com/wayneeseguin/rvm/master/binscripts/rvm-installer | bash -s stable
    source ~/.rvm/scripts/rvm
    rvm install 2.1.5
    rvm use 2.1.5 -- default
    gem install bundler
```

Follow this instruction http://rvm.io/integration/gnome-terminal

**Download BeEF**

```bash
    git clone git://github.com/beefproject/beef.git
```

**Install gems and launch**

```bash
    cd beef
    bundle install
    ruby beef
```

### Red Hat / Fedora

**Install dependencies**

```bash
    curl -sSL https://raw.githubusercontent.com/wayneeseguin/rvm/master/binscripts/rvm-installer | bash -s stable
    source ~/.rvm/scripts/rvm
    rvm install 2.1.5
    rvm use 2.1.5 --default
    gem install bundler
```

**Download BeEF**

```bash
    git clone git://github.com/beefproject/beef.git
```

**Install Gems and use it**

```bash
    cd beef
    bundle
    source ~/.bash_profile
    cd beef
    ./beef
```

**Alternative install method**

```bash
bash << curl -sSL https://raw.github.com/xntrik/beefcloud/master/beef-installer
source ~/.bash_profile
cd beef
./beef
```

### BackTrack

[[Look the dedicated page|BeEF-and-Backtrack-5]]

***

## Installation on MAC OS

**Install RVM and Ruby 2.1.5:**

```bash
    bash -s stable < <(curl -s https://raw.githubusercontent.com/wayneeseguin/rvm/master/binscripts/rvm-installer) source ~/.bash_profile
    rvm install 2.1.5 --with-gcc=clang
    rvm use 2.1.5
```

**Download BeEF**

You can download the [zip](https://github.com/beefproject/beef/zipball/master) or clone the git repository :

```bash
    git clone https://github.com/beefproject/beef.git
```

**Install Gems**

```bash
    bundle install
```
***

## Installation on MAC OS

**Install RVM and Ruby 2.1.5:**

```bash
    curl -sSL https://raw.githubusercontent.com/wayneeseguin/rvm/master/binscripts/rvm-installer | bash -s stable
    source ~/.rvm/scripts/rvm
    rvm install 2.1.5
    rvm use 2.1.5 --default
    gem install bundler
```

***
[[Previous|Architecture]] | [[Next|Configuration]]