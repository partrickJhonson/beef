By far the most common queries or issues our users encounter is how to get the dependancies BeEF requires up and running on their system with a minimum of hassle. While our [[installation guide|Installation]] includes instructions for most *Nix distributions we also put together LiveCD which includes a working install or BeEF, metasploit and sqlmap. 



## Using the LiveCD

Download here: (Link TBA)

To run, simply :

1. Download 
1. Create a new VM using your virtualisation software of choice.
1. Boot from the ISO. 
1. The console will automatically login with user beef and present you with a few options at startup:
1. Install & Setup SSH: this will enable SSH for remote acces to the VM and prompt you to create a password. 
1. Update BeEF (or metasploit/sqlmap) will update to the latest version available in GitHub 
1. Start beef

## Known Issues

Due to some issues running Ubuntu on VirtualBox users of VirtualBox may have to [toggle PAE Support](https://forums.virtualbox.org/viewtopic.php?f=7&t=6533)

## About the LiveCD

The liveCD based on Ubuntu 12.04 LTS and is configured to use Ruby 1.9.3p194. 

Apart from the standard install instructions (linked above) there is very little custom configuration of the OS.

[Ruby Version Manager](https://rvm.io/) was used to install and ruby versions, users can customize further and download, install and switch between Ruby versions with the rvm command on the LiveCD.

The LiveCD was generated using [Remastersys](http://www.remastersys.com/) and it's dist command, which generates the 850MB ISO file above. The custom splash screen and grub text are also customized by providing a custom splash.png and isolinug.cfg files. 

A reference to the liveCD/BeEFLive.sh file in the BeEF repository is added to the profile of the default user to prove the user with a series of friendly prompts, including updating or running beef. 


Any suggestions for other customizations or feature requests for the BeEF LiveCD? Let us know [@beefproject](https://twitter.com/beefproject) or raise issues for us in GitHub. 