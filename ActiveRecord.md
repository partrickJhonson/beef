### What is ActiveRecord?
Active Record is the model layer of the system which is responsible for representing the business data and logic.
This means it facilitates the creation and use of business objects whose data requires persistent storage to a database.
It is a Active Record pattern which is a description of a ORM system.

# Active Record Patter
In Active Record, objects carry both persistent data and behaviour which operates on that persistent data. Active Record is used in this way so that access logic being part of the object will educate users of that object on how to read and write from the database.

# ORM or Object Relational Mapping
ORM is a technique that connects the rich objects of an application to tables in a relational database management system. Using ORM means that an objects can be easily stored and retrieved from a database without writing SQL statements directly and with less overall database access code.

# ActiveRecord as an ORM
Active Record gives us several mechanisms, the most important being the ability to:

Represent models, their data, their relationship to other models, the inheritance through the related models, validating the models before they achieve persistence and perform those operations in an object oriented way.


# Migrations 
The Migrations for ActiveRecord are located in 
``
$ beef/core/main/ar-migrations
``

They look like this:
``
001_create_command_modules.rb
``
where the class looks like this:

    def change

        create_table :command_modules do |t|
            t.text :name 
            t.text :path
        end
    end


# Connects to DB

***
When Beef starts, in the setup file:
``
$beef/beef
``
It will load the the database by 
``
db_file = config.get('beef.database.file')
``
and it will then reset the database if it receives the -x flag.
The start file will then connect to the database and migrate if required.
See the file for more detailed information.

[Refer to the Database Schema](https://github.com/beefproject/beef/wiki/Database-Schema)

***

[[WebRTC Extension|WebRTC-Extension]] | [[Development Organization|Development Organization]]