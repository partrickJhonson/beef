RuboCop is a Ruby static code analyzer (a.k.a. linter) and code formatter. Out of the box it will enforce many of the guidelines outlined in the community Ruby Style Guide.

RuboCop's development is moving at a very rapid pace and there are often backward-incompatible changes between minor releases (since we haven't reached version 1.0 yet). To prevent an unwanted RuboCop update you might want to use a conservative version lock in your Gemfile:

gem 'rubocop', '~> 0.88.0', require: false

https://docs.rubocop.org/rubocop/0.88/index.html

