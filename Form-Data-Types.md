_Basic Data Types for Exploit Creation_

#### This information is outdated! ####

### Introduction ###

This page will detail the different type of input boxes that can be used in modules.

### Field Types ###

* textfield : Basic input field to accept a string (default)
* textarea : Larger text area to place > 255 characters of input
* hidden: hidden data that will be submitted with the form
* label: Text that will not be submitted but will be displayed to further explain input boxes
* checkbox : Basic Checkbox Datatype
* checkboxgroup: A group of checkboxes to be grouped together
* cobmobox : a pulldown select datatype 

### Field Properties ###

* name : the name of the field
* type : the field type (textfield, checkbox, combobox)
* ui_label : The text that labels the field on the form
* checked : set to 'true' if the default should be checked (checkbox only)
* html : html to be used for lables (label only)
* items : list of properties for checkboxgroups (checkboxgroup only)
* store_type : combobox store type (eg arraystore) (combobox only)
* store_fields : list of fields that describe the datastore for a combobox (combobox only)
* valueField : the name of the value items in store_fields (combobox only)
* displayField : the name of the display field in store_fields (combobox only)
* mode: the storage mode (eg local) for store_fields (combobox only)
* emptyText : The default text to be shown in a combobox (combobox only) 

### Example ###

```ruby
  def initialize
    super({
      'Name' => 'Demo Exploit',

      'Description' => %Q{
        This a demonstration exploit that won't do much
        },
      'Category' => 'Demo',
      'Author' => ['sussurro'],

       'Data' => [
               ['name' => 'textfield', 'type' => 'textield', 'ui_label' => 'textield input', 'value' =>'http://www.google.com'],
               ['name' => 'test_checkbox', 'type' => 'checkbox', 'ui_label' => 'checked', 'checked' => 'true'],
               ['name' => 'unchecked', 'type' => 'checkbox', 'ui_label' => 'unchecked'],
               ['type' => 'label', 'html' => 'THIS IS SOME LABEL DATA'],
               ['name' => 'checkboxgroup', 'type' => 'checkboxgroup', 'ui_label' => 'checkboxgroup', 'items' => [{:boxLabel => "cb1", 'name' => 'cb1'},{:boxLabel => 'cb2', 'name' => 'cb2'}]],
               ['name' => 'combokbox', 'type' => 'combobox', 'ui_label' => 'combobox','store_type' => 'arraystore', 'store_fields' => ['letters'], 'store_data' => [['a'],['b'],['c']], 'valueField' => 'letters', 'displayField' => 'letters' , 'mode' => 'local','emptyText' => "Select your favorite letter"],
  
    ],

      'File' => __FILE__,
    })
```
