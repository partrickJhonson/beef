## Preamble
If you're running Backtrack5-r2 BeEF IS working. The package maintainers did a great job on fixing all the issues below that were applicable to Backtrack5.

If you're running Backtrack5-r1, then we recommend you to update to release2, following this official guide written by muts and the other folks of OffensiveSecurity: http://www.backtrack-linux.org/backtrack/upgrading-to-backtrack-5-r2/

## Introduction
On BackTrack5 ( <= r1) both the old BeEF (PHP) and BeEF (Ruby) have been added but as we're doing a lot of development with a new alpha release every month, the (incorrectly named) BeEF-ng version is not up-to-date. Required gems are also not installed by default, and the gem environment is not configured correctly. This document will discuss how to setup this functionality.

NOTE 1: A script has been published to automate the steps described in this guide. Please see "**Backtrack 5 installation script**", bottom of the page.

NOTE 2: If you run tools that require ruby 1.8 you might the script "**Backtrack 5 change Ruby environment**" handy (bottom of the page)

## Installing BeEF from trunk in BT5
Following the next steps you will be able to use use the latest BeEF on your pentests using BT5: 

**1.**  _rm -rf/pentest/web/beef-ng_ 

**2.** _git clone git@github.com:beefproject/beef.git /pentest/web/beef_ 

**3.**  _GEM PATHS_  defined in the Gem Environment are wrong, so: 

add  _export GEM_PATH=/var/lib/gems/1.9.2/gems_   

and  _export GEM_HOME=/var/lib/gems/1.9.2/gems_   

to  _/etc/profile_ 

**4.**   _source /etc/profile_ 

**5.**  _cd /pentest/web/beef_ , then run   _ruby install_  , and press 2 to list all the required gems 

**6.** install these required gems with _gem install 'gem list from previous step'_ 

**7.** to see if everything went ok:
`

              root@bt:~# irb

              irb(main):001:0> require 'rubygems'

              => false

              irb(main):002:0> require 'dm-core'

              => true

              irb(main):003:0> Gem.path

              => ["/var/lib/gems/1.9.2/gems"]

              irb(main):004:0> quit
`
**8.** Start BeEF with the default SQLite DB:  _ruby beef -x_

Now BeEF is up-and-running and can be updated to the latest revision with the usual _git pull_ command from the /pentest/web/beef directory

## Backtrack 5 installation script
              #!/bin/sh
              #@author Abraham Aranguren <name.surname@gmail.com> http://securityconscious.blogspot.com
              #@comment Script to upgrade BeEF in Bactrack 5 based on the wiki steps here: https://github.com/beefproject/beef/wiki/BeEF-and-Backtrack-5

              DESTINATION="/pentest/web/beef"
              echo
              echo "Warning!!!: This will delete your $DESTINATION folder, press enter if you are sure, Control+C to cancel"
              echo "NOTE: By default Backtrack 5 has beef on /pentest/web/beef-ng instead"
              read intputvar

              echo "Checking internet connectivity ..."
              INTERNET=$(host www.google.com|grep "timed out"|wc -l)
              if [ $INTERNET -eq 1 ]; then
                      echo
                      echo "You need internet connectivity to download the latest BeEF version from the internet"
                      echo "It looks like you have no internet connectivity. If you are lazy use the following command:"
                      echo "/etc/init.d/networking start"
                      exit
              else
                      echo "Internet connectity OK"
              fi

              echo
              echo "Upgrading BeEF..."
              rm -rf $DESTINATION
              git clone git@github.com:beefproject/beef.git $DESTINATION
              cd $DESTINATION
              #Select option 2: ruby1.9.2
              #2            /usr/bin/ruby1.9.2   400       manual mode
              echo
              echo "Selecting option 2: ruby1.9.2 .."
              echo
              (sleep 1 ; echo 2) | update-alternatives --config ruby
              echo
              echo "Installing BeEF .."
              echo
              (sleep 2 ; echo 2) | ruby install > tmpfiledeleteme.txt

              #Present info to the user
              cat tmpfiledeleteme.txt

              command=$(tail -2 tmpfiledeleteme.txt|grep gem)
              rm -f tmpfiledeleteme.txt

              echo
              echo "Modifying /etc/profile to include correct Gem paths ..."
              echo
              gempaths="export#GEM_PATH=/var/lib/gems/1.9.2/gems export#GEM_HOME=/var/lib/gems/1.9.2/gems" #works
              #gempaths="export#GEM_PATH=/var/lib/gems/1.9.2 export#GEM_HOME=/var/lib/gems/1.9.2" #works too
              for i in $gempaths; do
                      line=$(echo $i | sed 's/#/ /g')
                      nummatches=$(grep "$line" /etc/profile|wc -l)
                      if [ $nummatches -eq 0 ]; then # Check config line is not there yet, if not there add it
                              echo "$line" >> /etc/profile
                      fi
              done

              source /etc/profile
              #Load these new environment variables
              . /etc/profile

              echo
              echo "Installing Gems ..."
              echo
              $command
              #Issue 496 Fix: Added erubis gem installation by hand as otherwise this does not work in BT5 R1:
              gem install erubis

              echo
              echo "Verifying installation was successful, please review this!"
              echo "require 'rubygems' -> should be 'false'. require 'dm-core' -> should be 'true'. Gem.path should be [\"/var/lib/gems/1.9.2/gems\"]"
              echo
              #Now check things are working
              (sleep 2; echo "require 'rubygems'"; sleep 1; echo "require 'dm-core'"; sleep 1; echo Gem.path ; sleep 1; echo quit)|irb

              echo
              echo "IMPORTANT!!: If you did not run this script with '. ' at the beginning please run the following command so that Gem paths are correctly set:"
              echo ". /etc/profile"
              echo
              echo "To start BeEF with the default SQLite DB use the following command:"
              echo "ruby beef -x"
              echo

## Backtrack 5 change Ruby environment

Some Backtrack 5 security tools need ruby 1.8 (i.e. whatweb) and others ruby 1.9.2 (i.e. BeEF). This script automates the switch. 

By setting the ruby environment to the correct ruby version we can run all the tools. This script aims to make this small task easier to do and in a more scripting-friendly way. 

###Installation Instructions: 
copy-paste code below into a file called setrubyenv.sh, ideally somewhere in your PATH 
_chmod 700 setrubyenv.sh_ # (obviously!) 


**IMPORTANT**: You need to call this script with a ". " in front of it to alter your environment settings.

              #!/usr/bin/env bash
              # Description:
              # Some tools (metasploit, whatweb and others) require ruby 1.8 and others (i.e. BeEF) require ruby 1.9.2
              # This script allows you to quickly change from ruby 1.8 to 1.9.2 and viceversa
              #
              # Author abraham.aranguren < abraham dot aranguren _ a t_ gmail d o t com > http://securityconscious.blogspot.com


              if [ $# -ne 1 ]; then
                      echo "Syntax: $0 <ruby_version: 1.8, 1.9.2>"
                      echo 
                      echo "Examples:"
                      echo "- Set ruby 1.8: $0 1.8"
                      echo "- Set ruby 1.9.2: $0 1.9.2"
                      exit
              fi

              VERSION=$1
              echo $VERSION

              OPTION="1"
              if [ '1.9.2' == $VERSION ]; then
                      OPTION="2"
              fi

              # Export version gem paths
              export GEM_PATH=/var/lib/gems/$VERSION/gems
              export GEM_HOME=/var/lib/gems/$VERSION/gems
              # Pick ruby version
              #(sleep 2 ; echo $OPTION) | update-alternatives --config ruby > /dev/null
              (sleep 2 ; echo $OPTION) | update-alternatives --config ruby