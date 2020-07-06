# Target System Compatibility

Considering the nature of BeEF's use cases, it is important that we ensure the compatibility among a broad spectrum of operating systems and browsers. Please note that this compatibility is not in reference to host system installation of BeEF, rather the target systems been looks to hook.

## BrowserStack

BeEF runs automated testing on Travis-CI whenever a merge request is raised. One component of this automated testing is running any client side code (e.g. [Command Module](https://github.com/beefproject/beef/wiki/Module-Creation) testing) through [BrowserStack](https://www.browserstack.com/).

BrowserStack allows us to run our code through through a matrix of browsers/operating systems ensuring any update to the BeEF codebase will run on broad set of target environments. This practice helps us to maintain a more stable master branch, and sets a baseline for the quality of code in pull requests.

Open Source licencing restrictions on Travis-CI prevent us from running a full suite of compability testing. Our aim is to get the best end to end coverage possible within the bounds of these restrictions, prioritising the latest and most recent minimum compatible version per operating system/browser.

See the compatibility matrix below:

|                | Chrome         | Firefox            | Safari | Edge | Internet Explorer |
|---             |:---:           |:---:               |:---:   |:---: |:---:              |
| **OSX**        |                |                    |        |      |                   |
| Catalina       | 81<br>59<br>41 | 75<br>68 ESR<br>11 | 13     | -    | -                 |
| El Capitan     | 81<br>14       | 75<br>7            | 9.1    | -    | -                 |
| Snow Leopard   | 49<br>35<br>14 | 42<br>38 ESR<br>7  | 5.1    | -    | -                 |
| **Windows**    |                |                    |        |      |                   |
| 10             | 81<br>59<br>37 | 75<br>68 ESR<br>32 | -      | 81   | 11                |
| 8              | 81<br>22       | 75<br>32           | -      | 81   | 10                |
| XP <sup>†</sup>| 43<br>28<br>14 | 47<br>26<br>16     | -      | -    | 7                 |

*<sup>†</sup> Please note BrowserStack does not support the most current version of Firefox ESR for Windows XP so we are unable to test it at this time (27/04/20).*

***
[[BeEF Testing|BeEF Testing]] | [[Database Schema|Database Schema]]
