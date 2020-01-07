## Introduction

BeEF'S [RESTful API]( https://github.com/beefproject/beef/wiki/BeEF-RESTful-API) has a postman file and environment available for you to use! Postman allows users to very quickly and easily send requests to API endpoints. This means you can use BeEF without the graphical interface. 

## Installing Postman
### Ubuntu
Postman is very simple to install on ubuntu, simply run:
```bash
$ snap install postman 
$ postman
```
### Other Systems
Postman can be downloaded directly from their website: https://www.getpostman.com/downloads/.

## Using Postman

Once you have Postman and [BeEF](https://github.com/beefproject/beef/wiki/Installation) installed and running, simply select _File > Import_ and import the BeEF RESTful API json file. Once you have this opened, you should see “RESTful API” in your collections on the left. Click on this and you’ll see a list of all of the API requests available to you.

In order to execute any of these you need to import and set up your environment variables. Import the environment variables in _File > Import_ and find the "BeEF postman environment .JSOn file". Once imported, in the top right corner, you should now see “BeEF” with a drop down arrow.  Select the eye symbol next to it and you will see a variety of variables to set up. The variables you should see are:

### Username and Password
In the current value section of the Username and Password fields.
Enter your username and password that you set up in the config.yaml file of the BeEF directory.

### Token

By sending an [authentication request](https://github.com/beefproject/beef/wiki/BeEF-RESTful-API#authentication), you will receive back a token which is stored in your environment variables. This can also be found in the console when you run BeEF, it should look like the below: 
```bash
[*] RESTful API key: a1403452cf5d552f1cf53ae0c125adfffc0acc5c
```

### Session_id

Each browser has it’s own session ID. By sending the _“Get All Hooked Browsers”_ request, information on the hooked browsers will be returned, including the session ID. Store the session ID of the browser you’d like to send requests to in the environment variables. 

### Module_id

By sending the request labelled “List All Command Modules” this will list all available modules/BeEF commands and their ID’s. Select the module you’d like to run and use the id associated with it.

### Cmd_id

Each time a command is executed, it is assigned an ID. To identify the command ID, just look in the response when you execute a command. It will look like this:
```bash
{
    "success": "true",
    "command_id": "3"
}
```

### Dnsrule_id

The DNS rule ID can be found by send a post requested labelled _“List the DNS Ruleset”_. This will list all created DNS rules and their associated ID’s. 

