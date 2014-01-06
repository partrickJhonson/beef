## Installation on Windows

**Install dependencies**

* Download and Install: http://rubyinstaller.org/
* (Including the Development Kit, for more info see here: https://github.com/oneclick/rubyinstaller/wiki/Development-Kit)
* Download and Extract into your Ruby BIN folder: http://www.sqlite.org/sqlitedll-3_7_0_1.zip
* Add your Ruby BIN folder to your system PATH variable.
* Open a command Prompt and browse to where you extracted the Development Kit, run:
'''ruby dk.rb init'''
and
'''ruby dk.rb install'''
* Follow the steps described here: https://github.com/hiranpeiris/therubyracer_for_windows
This is needed because the admin UI is using the Uglifier gem, which needs a JavaScript environment. This is quite painful to install in Windows, so that link provides pre-compiled DLLs for the v8 engine and 2 required gems.
* Browse to where you extracted BeEF and run:
'''gem install bundler'''
* At this stage you should have the following gems installed:
'''
bundler (1.5.1)
ref (1.0.5)
therubyracer (0.11.0beta1 x86-mingw32)
'''
* You're now ready for the last step. After that, you can start BeEF.
'''bundle install'''


***

## Installation on Linux

### Debian / Ubuntu

**Install dependencies**

```bash
    sudo apt-get update 
    sudo apt-get install curl git ruby build-essential libsqlite3-ruby libsqlite3-dev libssl-dev
    sudo curl https://raw.github.com/wayneeseguin/rvm/master/binscripts/rvm-installer | bash -s stable
    sudo echo [[ -s "$HOME/.rvm/scripts/rvm" ]] && . "$HOME/.rvm/scripts/rvm" # Load RVM function' >> ~/.bash_profile 
    sudo source ~/.bash_profile
    rvm pkg install zlib --verify-downloads 1
    rvm use 1.9.3
    gem install bundler
```

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
    sudo yum install -y git make gcc openssl-devel gcc-c++ patch readline readline-devel zlib zlib-devel libyaml-devel libffi-devel bzip2 autoconf automake libtool bison iconv-devel sqlite-devel
    wget https://raw.github.com/wayneeseguin/rvm/master/binscripts/rvm-installer
    bash ./rvm-installer
    source ~/.rvm/scripts/rvm
    rvm pkg install openssl
    rvm install 1.9.2 --with-openssl-dir=$rvm_path/usr
    source ~/.rvm/scripts/rvm
    rvm use 1.9.2 --default
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
bash << curl -s https://raw.github.com/xntrik/beefcloud/master/beef-installer
source ~/.bash_profile
cd beef
./beef
```


### BackTrack

[[Look the dedicated page|BeEF-and-Backtrack-5]]

***

## Installation on MAC OS

**Install RVM and Ruby 1.9.3:**

```bash
    bash -s stable < <(curl -s https://raw.github.com/wayneeseguin/rvm/master/binscripts/rvm-installer) source ~/.bash_profile
    rvm install 1.9.3-p0 --with-gcc=clang
    rvm use 1.9.3
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

[[See detailed instruction on MAC OS X installation|MAC-OSX-installation-using-RVM]]

***
[[Previous|Architecture]] | [[Next|Configuration]]