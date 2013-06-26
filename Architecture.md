_The Architecture of the BeEF System_

### Introduction ###

The following diagrams and explanations should explain how BeEF works and the different ways you can use it. This page will be updated as new functionality is introduced in each release.

### High Level ###

[[/Images/BeEF_Overall.png|align=center]]

When a user runs up BeEF currently, there are two components started: the User Interface and the Communication Server. These two components are the base components of BeEF and are discussed in detail below.

### Components ###

[[/Images/BeEF_Components.png|align=center]]


**User Interface**

This is the control interface for using BeEF. From here a user can see all online and offline browsers, run exploits against them and see the results (Pattern 1).

**Communication Server**

This guy is essential to how BeEF works. The Communication Server (CS) is the component that communicates via HTTP with the hooked browsers.

### Usage Pattern 1 ###

[[/Images/Pattern1.png|align=center]]

This is the most basic usage pattern for BeEF. An attacker simply need run up BeEF (`beef.rb`) and login directly to the UI. From here the attacker can see which hooked browsers are online and which are offline, all information collected about/from a particular hooked browser, and run exploits against online hooked browsers.

***
[[Previous|Introducing-BeEF]] | [[Next|Installation]]