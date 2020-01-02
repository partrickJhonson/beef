## Introduction
WebRTC stands for Web Realtime Communications and allows for peer-to-peer communications between two web browsers. The code for the WebRTC Extension can be found [here.](https://github.com/beefproject/beef/tree/master/extensions/webrtc)

## Configuration
```bash
beef:
    extension:
        webrtc:
            name: 'WebRTC'
            enable: false
            authors: ["xntrik"]
            stunservers: '["stun:stun.l.google.com:19302","stun:stun1.l.google.com:19302","turn:numb.viagenie.ca:3478"]'
            # stunservers: '["stun:stun.l.google.com:19302"]'
            turnservers: '{"username": "someone%40somewhere.com", "password": "somepass", "uris": ["turn:numb.viagenie.ca:3478?transport=udp","turn:numb.viagenie.ca:3478?transport=tcp"]}'

```

## Utilization 
WebRTC can be used to retrieve the internal (behind NAT) IP address of the victim machine, using the peer-to-peer connection framework. This command can be found under the Host module folder.

***
[[Module Creation|Module-creation]] | [[Development Organization|Development-Organization]]