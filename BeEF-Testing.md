## Introduction
Testing is important in every serious software development process. Although in BeEF we don't use TDD (Test-driven development), we do have a testing suite. 

BeEF tests are all contained inside `<beef_root>/test` directory.
A Rakefile, `<beef_root>/Rakefile`, contains testing tasks, organized by categories.

To run all tests, run (from `<beef_root>`):

`rake all`

Otherwise, to run only some testing categories, for instance 'integration', run:

`rake integration`

Before running the tests locally on your machine, it's mandatory that you change in <beef_root>/test/common/test_constants.rb the values of ATTACK and VICTIM_DOMAIN, to something like:
```ruby
ATTACK_DOMAIN = "127.0.0.1"
VICTIM_DOMAIN = "127.0.0.1"
```
On our continuos integration server, responsible to run all the tests suite on every GIT change, these constants already contain the proper default values. When you change these values for your local tests, be sure to don't commit/push these changes to the BeEF repo.

## Testing categories
The BeEF testing framework is a mix of 2 types of tests:
 - unit tests
 - functional tests

We currently have the following testing categories:
 - **integration**: mainly functional tests. We use Capybara and WebDriver in order to instrument the browser to do stuff for us. Whe running these tests, you will see a browser being open (currently Firefox, we're working on extendind the testing suite including all the other browser). The integration testing quite is responsible to run functional tests on the Web GUI and test module execution.

 - **unit**: as the word says, mainly unit tests. Things like the directory structure, default config options and basic components like the network_handler are tested.
 
 - **thirdparty/msf**: contains Metasploit related test files. With these tests Metasploit is started, connectivity and authentication to msgrpc is tested.

You will also notice another directory, **common**. As the name suggests, it contains things shared across testing suites, for instance constants and methods.

## Unit tests
When writing unit tests, you will mainly use two functions:

assert(Boolean) -> test pass if the Boolean condition is true.
For example:

```ruby
a = 1
b = 2
```
Test OK.
```ruby
assert(a == b)
```
Test FAIL.
```ruby
assert(not(a == b))
```
To check if a code block hasn't raised (or throwned, as you prefer :-) any exception:
```ruby
assert_nothing_raised do
    something
end
```
## Functional tests

For functional tests, other than using some aspects of the unit tests, we use Capybara and Selenium-WebDriver. The result is the possibility to programmatically control a browser (at the moment Firefox, we're working to improve our testing suite with Webkit and other browsers) from a user's point-of-view. For instance, we're able to instrument the browser to login into the BeEF Web GUI, as you can see here below:
```ruby
  def self.login(session = nil)
    session = Capybara::Session.new(:selenium) if session.nil?
    session.visit(ATTACK_URL)
    sleep 2.0
    session.has_content?('BeEF Authentication')
    session.fill_in 'user', :with => 'beef'
    session.fill_in 'pass', :with => 'beef'
    session.click_button('Login')
    sleep 20.0

    session
  end
```
### Testing command modules
