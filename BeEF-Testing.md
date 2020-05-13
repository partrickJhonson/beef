## Introduction
Testing is important in every serious software development process. Although in BeEF we don't use TDD (Test-driven development), we do have a testing suite. 
Before running the tests locally on your machine, you must install necessary gems:

```
export BEEF_TEST=true
bundle install --with test
```

BeEF tests are all contained inside `<beef_root>/spec` directory.
A Rakefile, `<beef_root>/Rakefile`, contains testing tasks, organized by categories.

To run all tests, run (from `<beef_root>`):

`bundle exec rake --all`

Otherwise, to run only some testing categories, for instance 'spec', run:

`bundle exec rake spec`

Before running the tests locally on your machine, you may want to change the values of ATTACK_DOMAIN and VICTIM_DOMAIN in `<beef_root>/spec/support/constants.rb`, to something like:

```ruby
ATTACK_DOMAIN = "127.0.0.1"
VICTIM_DOMAIN = "localhost"
```
These values must differ, however it is acceptable if both resolve to the same host.

On our continuous integration server, responsible to run all the tests suite on every GIT change, these constants already contain the proper default values. When you change these values for your local tests, be sure not to commit/push these changes to the BeEF repository.

## Testing Categories
The BeEF testing framework is a mix of 2 types of tests:
 - rspec tests
 - functional tests

To run these tests just on their own run:
`bundle exec rake`
and the specific category, for example:
`bundle exec rake rdoc`
To run rdoc.

We currently have the following testing categories:
- **ssl:**: creates a new SSL certificate and Re-generate the SSL certificate
- **rdoc:**: creates the rdoc information
- **beef_start:**: sets up and starts BeEF
- **beef_stop:**: cleanup and stops beef
- **msf_start:**: starts the msf_console
- **msf_stop:**:kills the MSF_process
- **msf_update:**: git pulls the msf repo
- **dmg:**: creates the Mac DMG file
- **cde:**: this will download and make the CDE Executable plus generate a cde package in cde-package
- **cde_beef_start:**: starts the CDE/beef enviorment set-up
- **db:**: requires the :environment to require beef

## Running (temporarily) skipped tests

RSpec tests that are defined with `xit` is skipped. If you would like to run those tests, change `xit` to `it` and it will run.

e.g. as of Jan-17-2020, `spec/beef/extensions/requester_spec.rb` has a functional test that is skipped by default.
```
# change this
xit 'requester works' do

# to this
it 'requester works' do
```


## Unit Tests
When writing unit tests, you will mainly use two functions:

assert(Boolean) -> test pass if the Boolean condition is true.
For example:

```ruby
a = 1
b = 1
```
Test OK.
```ruby
assert(a == b)
# you can also use
assert_equal a,b
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
## Functional Tests

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
    sleep 10.0

    session
  end
```
### Testing Command Modules
In order to inject custom JavaScript into the hooked browser during testing, you have 2 choices:
 - **execute_script** : available from objects of type Capybara::Session. It comes in handy when the JavaScript you want to inject is actually returning something. Example:
```javascript
def test_jools_simple
        victim = BeefTest.new_victim
        script = " var ciccio = 'ciccio';
            ciccio += '_pasticcio';
            return ciccio;"
       result = victim.execute_script(script)
       assert_equal result,'ciccio_pasticcio'
    end
```
 - **RESTful API** : as you can launch command modules, and retrieve results through the RESTful API, you can also use it for testing purposes. This is particularly effective when the JavaScript to be injected in the hooked browser is complex or it's not explicitly returning a value (i.e.: returning data using only beef.net.send()). For example, to test the execution of a module (in this case a Debug module), see the following example. Also, have a look at `<beef_root>/test/integration/tc_debug_modules.rb` in order to see how some variables like `hb_session`, `token` and others are retrieved from previous tests.

```ruby
## Test debug module "Test_return_long_string" using the RESTful API
  def test_return_long_string
    repeat_string = "BeEF"
    repeat_count = 20

    response = RestClient.post "#{RESTAPI_MODULES}/#{@@hb_session}/#{@@mod_debug_long_string}?token=#{@@token}",
                               { 'repeat_string' => repeat_string,
                                 'repeat'        => repeat_count}.to_json,
                               :content_type => :json,
                               :accept => :json
    assert_equal 200, response.code
    assert_not_nil response.body
    result = JSON.parse(response.body)
    success = result['success']
    assert success

    cmd_id = result['command_id']
    count = 0
    response = RestClient.get "#{RESTAPI_MODULES}/#{@@hb_session}/#{@@mod_debug_long_string}/#{cmd_id}?token=#{@@token}"

    while(response.body.size <= 2 && count < 10)
      response = RestClient.get "#{RESTAPI_MODULES}/#{@@hb_session}/#{@@mod_debug_long_string}/#{cmd_id}?token=#{@@token}"
      sleep 2
      count += 1
    end
    assert_equal 200, response.code
    assert_not_nil response.body
    result = JSON.parse(response.body)
    data = JSON.parse(result['0']['data'])['data']
    assert_not_nil data
    assert_equal data,(repeat_string * repeat_count)
  end
```

### Testing Metasploit

To test Metasploit integration, run:
`bundle exec rake msf_start`

This will clone the latest version of Metasploit to /tmp/msf-test/


### Check Ruby Gems

To check Ruby Gems for known vulnerabilities, run:
`bundle exec rake bundle_audit`



## Conclusion
We are actively working to improve the BeEF testing suite and exploring other testing solutions. For any trouble, do not hesitate to contact us via email/twitter or by raising a ticket in Github!

***
[[Creating An Extension|Creating An Extension]] | [[Database Schema|Database Schema]]