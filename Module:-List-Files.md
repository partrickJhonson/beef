## Summary

* **Objective**: List files via PhoneGap API
* **Authors**: mh
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/phonegap/phonegap_list_files)

## Internal Working

Uses the PhoneGap API to inspect the file system.

```js

// use directoryentry to create directory reader
function gotDirEntry(dirEntry) {
    var directoryReader = dirEntry.createReader();
    directoryReader.readEntries(success,fail);
}

// use getDirectoy to create reference to directoryentry
function gotFS(fileSystem) {
    fileSystem.root.getDirectory(directory, null, gotDirEntry, fail);
}

```


## Feedback

