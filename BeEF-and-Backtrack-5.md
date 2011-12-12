## Introduction
On BackTrack5 both the old BeEF (PHP) and BeEF (Ruby) have been added but as we're doing a lot of development with a new alpha release every month, the (incorrectly named) BeEF-ng version is not up-to-date. Required gems are also not installed by default, and the gem environment is not configured correctly. This document will discuss how to setup this functionality.

NOTE 1: A script has been published to automate the steps described in this guide.

NOTE 2: If you run tools that require ruby 1.8 you might find this script handy

## Installing BeEF from trunk in BT5
Following the next steps you will be able to use use the latest BeEF on your pentests using BT5: 
**1.**  _ rm -rf/pentest/web/beef-ng  _ 
**2.** _ svn check_out http://beef.googlecode.com/svn/trunk/ /pentest/web/beef _ 
**3.**  _ GEM PATHS _  defined in the Gem Environment are wrong, so: add  _ export GEM_PATH=/var/lib/gems/1.9.2/gems _   and   _ export GEM_HOME=/var/lib/gems/1.9.2/gems _   to  _ /etc/profile  _ 
**4.**   _ source /etc/profile  _ 
**5.**  _ cd /pentest/web/beef _ , then run   _ ruby install _  , and press 2 to list all the required gems 
**6.** install these required gems with gem install 'gem list from previous step' 
**7.** to see if everything went ok:
`root@bt:~# irb
        irb(main):001:0> require 'rubygems'
        => false
        irb(main):002:0> require 'dm-core'
        => true
        irb(main):003:0> Gem.path
        => ["/var/lib/gems/1.9.2/gems"]
        irb(main):004:0> quit`
**8.** Start BeEF with the default SQLite DB:  ruby beef -x

Now BeEF is up-and-running and can be updated to the latest trunk version with the usual  svn update  command from the /pentest/web/beef directory