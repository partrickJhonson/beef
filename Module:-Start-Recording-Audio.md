## Summary
* **Objective**: start recording audio to a file
* **Authors**: Mike Haworth
* **Browsers**: any with Adobe Phonegap
* [[Code|https://github.com/beefproject/beef/tree/master/modules/phonegap/phonegap_start_record_audio]]

## Internal Working

starts recording to a local file

```js

var file_uri = "<%== @file_name %>";

m = new Media(file_uri);
m.startRecord();
```

## Feedback