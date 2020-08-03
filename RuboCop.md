BeEF is going to be following the baseline Rubocop style guide, V 0.88.0!

In order to change the version we will have to discuss it, ideally getting BeEF to passing Rubocop 0.88.0 first.

RuboCop is a Ruby static code analyzer (a.k.a. linter) and code formatter. Out of the box it will enforce many of the guidelines outlined in the community Ruby Style Guide.

The conservative version  that we are using in our Gemfile is:

gem 'rubocop', '~> 0.88.0', require: false

You can run Rubocop by going to the root directory of beef and running:
`
rubocop
`
See the docs below for more information 

https://docs.rubocop.org/rubocop/0.88/index.html

