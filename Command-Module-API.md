_This page details the Command Module API_

### Introduction ###

The framework allows command modules to set and get details about the hooked browser. Details set from the results of one module may be used to better target another. The base class `BeEF::Command` has the two more methods: `set_browser_details()` and `get_browser_detail()`.

### Example ###

For example, a module might use `get_browser_detail('UA')` which returns the user agent. Then the code may vary to better target the browser.

### Alert Command Module ###

Adding the following code to the alert module will demonstrate the usage of the Command Module API.

```ruby
def pre_send
  browser_name = get_browser_detail('BrowserName')
  @datastore['text'] = 'your browser is (' + browser_name + '): ' + @datastore['text']
end

def callback
  content = {}
  content['User Response'] = "The user clicked the 'OK' button when presented with an alert box saying: '"
  content['User Response'] += @datastore['text'] + "'"
  
  set_browser_detail("OKDialog", "User Clicks OK")
  
  save content
end
```