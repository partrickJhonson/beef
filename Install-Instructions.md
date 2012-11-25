# Installation Instructions

This page details installation of prerequisite software (Namely Ruby 1.9, Sqlite and Required Gems) for common operating systems.

## Mac OSX

To install RVM and Ruby 1.9.3 on Mac OS: <br> 
$ bash -s stable < <(curl -s https://raw.github.com/wayneeseguin/rvm/master/binscripts/rvm-installer) source ~/.bash_profile<br> 
$ rvm install 1.9.3-p0 --with-gcc=clang<br> 
$ rvm use 1.9.3<br> 
(Download and navigate to beef directory)<br> 
$ bundle install<br> 
$ ruby beef 

## Redhat / Fedora Linux

### Method 1
$ bash < <(curl -s https://raw.github.com/xntrik/beefcloud/master/beef-installer)<br> 
$ source ~/.bash_profile<br> 
$ cd beef<br> 
$ ./beef<br> 

### Method 2

$ sudo yum install -y git make gcc openssl-devel gcc-c++ patch readline readline-devel zlib zlib-devel libyaml-devel libffi-devel bzip2 autoconf automake libtool bison iconv-devel sqlite-devel<br> 
$ wget https://raw.github.com/wayneeseguin/rvm/master/binscripts/rvm-installer<br> 
$ bash ./rvm-installer<br> 
$ source ~/.rvm/scripts/rvm<br> 
$ rvm pkg install openssl<br> 
$ rvm install 1.9.2 --with-openssl-dir=$rvm_path/usr<br> 
$ source ~/.rvm/scripts/rvm<br> 
$ rvm use 1.9.2 --default<br> 
$ gem install bundler<br> 
$ git clone git://github.com/beefproject/beef.git<br> 
$ cd beef<br> 
$ bundle<br> 
$ source ~/.bash_profile<br> 
$ cd beef<br> 
$ ./beef<br> 


## Debian / Ubuntu

### Method 1 

$ sudo apt-get update<br> 
$ sudo apt-get install curl git ruby build-essential libsqlite3-ruby libsqlite3-dev libssl-dev<br> 
$ sudo curl https://raw.github.com/wayneeseguin/rvm/master/binscripts/rvm-installer | bash -s stable<br> 
$ sudo echo '[[ -s "$HOME/.rvm/scripts/rvm" ]] && . "$HOME/.rvm/scripts/rvm" # Load RVM function' >> ~/.bash_profile<br> 
$ sudo source ~/.bash_profile<br> 
$ rvm pkg install zlib --verify-downloads 1<br> 
$ rvm install 1.9.3 <br> 
$ rvm use 1.9.3<br> 
$ gem install bundler<br> 
$ git clone git://github.com/beefproject/beef.git<br> 
$ cd beef<br> 
$ bundle install<br> 
$ ruby beef<br>

### Method 2 (If no previous version of Ruby is installed or needed)

$ sudo apt-get update<br> 
$ sudo apt-get install ruby1.9.1-dev build-essential libsqlite3-ruby libsqlite3-dev build-essential libsqlite3-ruby git libsqlite3-dev  <br> 
$ git clone git://github.com/beefproject/beef.git<br> 
$ cd beef<br> 
$ sudo gem install bundler<br> 
$ sudo bundle install<br> 
$ ruby beef<br> 




      