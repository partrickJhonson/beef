_The Architecture of the BeEF System_

### Introduction ###

The following diagrams and explanations should explain how BeEF works and the different ways you can use it. This page will be updated as new functionality is introduced in each release.

### High Level ###

![https://beef.googlecode.com/svn/wiki/img/BeEF_Overall.png](https://beef.googlecode.com/svn/wiki/img/BeEF_Overall.png)

When a user runs up BeEF currently, there are two components started: the User Interface and the Communication Server. These two components are the base components of BeEF and are discussed in detail below. 

### Components ###

![https://beef.googlecode.com/svn/wiki/img/BeEF_Components.png](https://beef.googlecode.com/svn/wiki/img/BeEF_Components.png)

**User Interface**

This is the control interface for using BeEF. From here a user can see all [[online|https://github.com/beefproject/beef/wiki/Online-Hooked-Browser]] and [[offline|https://github.com/beefproject/beef/wiki/Offline-Hooked-Browser]] browsers, run exploits against them and see the results (Pattern 1). 

**Communication Server**

This guy is essential to how BeEF works. The Communication Server (CS) is the component that communicates via HTTP with the [[hooked browsers|https://github.com/beefproject/beef/wiki/Hooked-Browser]].

### Usage Pattern 1 ###

![https://beef.googlecode.com/svn/wiki/img/Pattern1.png](https://beef.googlecode.com/svn/wiki/img/Pattern1.png)

This is the most basic usage pattern for BeEF. An attacker simply need run up BeEF (`beef.rb`) and login directly to the UI. From here the attacker can see which [[hooked browsers|https://github.com/beefproject/beef/wiki/Hooked-Browser]] are [[online|https://github.com/beefproject/beef/wiki/Online-Hooked-Browser]] and which are [[offline|https://github.com/beefproject/beef/wiki/Offline-Hooked-Browser]], all information collected about/from a particular [[hooked browser|https://github.com/beefproject/beef/wiki/Hooked-Browser]], and run exploits against online [[hooked browsers|https://github.com/beefproject/beef/wiki/Hooked-Browser]]. 
