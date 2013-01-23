## Introduction
Testing is important in every serious software development process. Although in BeEF we don't use TDD (Test-driven development), we do have a testing suite. 

BeEF tests are all contained inside `<beef_root>/test` directory.
A Rakefile, `<beef_root>/Rakefile`, contains testing tasks, organized by categories.

To run all tests, run (from `<beef_root>`):
`rake all`

Otherwise, to run only some testing categories, for instance 'integration', run:
`rake integration`

## Testing categories
The BeEF testing framework is a mix of 2 types of tests:
 - unit tests
 - functional tests

We currently have the following testing categories:
 - integration: mainly functional tests. We use Capybara and WebDriver in order to instrument the browser to do stuff for us. Whe running these tests, you will see a browser being open (currently Firefox, we're working on extendind the testing suite including all the other browser). The integration testing quite is responsible to run functional tests on the Web GUI and test module execution.

 - unit: as the word says, mainly unit tests. Things like the directory structure, default config options and basic components like the network_handler are tested.
 
 - msf: contains Metasploit related test files. With these tests Metasploit is started, connectivity and authentication to msgrpc is tested.

## Unit tests
When writing unit tests, you will mainly use two functions:

assert(Boolean) -> test pass if the Boolean condition is true.
For example:

`a = 1
b = 2`

`assert(a == b)` -> test pass

`assert(not(a == b))` -> test fails

To check if a code block hasn't raised (or throwned, as you prefer :-) any exception:

`assert_nothing_raised do
    something
end`

## Functional tests

blabla