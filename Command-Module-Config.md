
### Introduction ###

All command modules require a config file which contains the basic configuration settings BeEF needs in order to load and execute the module.

This file is used by the framework to set the category, name, description and valid targets for the module.


### Details ###

The config file is in YAML format. It must exist in the same directory as the command module and must be named "config.yaml".

Note that white-space is not allowed within a node name and tab characters cannot be used for indentation. A space is mandatory when separating strings within an array, for example: {{{authors: ["pdp", "wade", "bm", "xntrik"]}}}.


### Example ###

Below is an example of a command module config file.

```ruby
beef:
    module:
        detect_local_settings:
            enable: true
            category: "Network"
            name: "Detect Local Settings"
            description: "Grab the local network settings (ie internal ip address)."
            authors: ["pdp", "wade", "bm", "xntrik"]
            target:
                working: ["FF", "IE"]
                user_notify: "C"
                not_working: "S"

```

### Format ###

The first and second nodes must be "beef" and "module" respectively, followed by the module name as the third node, for example:

```ruby
beef:
    module:
        detect_local_settings:
```

The "enable" node contains a Boolean value. If set to "true" it tells the framework to enable the module and show it in the command modules tree.
```ruby
enable: true
```

The "category" node determines the category in which the command module will be displayed in the command modules tree.
```ruby
category: "Network"
```

The "name" node determines the command module's name.
```ruby
name: "Detect Local Settings"
```

The "description" node determines the text to be displayed when the user selects the module.

```ruby
description: "Grab the local network settings (ie internal ip address)."
```

### Target ###

The "target" node is mandatory. This node determines which browsers the module has been confirmed to work with. It has many child-nodes which may contain strings or arrays, for example:

```ruby
target:
    working: ["FF", "IE"]
    user_notify: "C"
    not_working: "S"
```

When only some browser versions or operating systems are compatible the "target" node may also contain "min_ver", "max_ver" and "os" child-nodes.

The final target value of a browser/command module is determined through a rating mechanism. If there are multiple matches, the first target config will apply, for example, using a more complicated example:

```ruby
target:
    not_working:
        ALL:
            os: ["iPhone"]
    working: ["O", "FF", "S", "IE"]
    user_notify: ["C"]
```

In this instance, an iPhone running Safari would match both not_working and working, but as not_working is first, that would be the final rating for a module with this particular target configuration.

The final rating is converted into an icon in BeEF:

* Green (VERIFIED_WORKING) for works
* Orange (VERIFIED_USER_NOTIFY) for user will be notified
* Red (VERIFIED_NOT_WORKING) for doesn't work
* Grey (VERIFIED_UNKNOWN) for unknown
***
[[Database Schema|Database Schema]] | [[Command Module API|Command Module API]]
