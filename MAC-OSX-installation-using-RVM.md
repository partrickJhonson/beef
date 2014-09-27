A friend of mine (antisnatchor), Mike Ryan (@justfalter), wrote this amazing step-by-step guide on how to install BeEF on MacOSX using RVM.
It's very clear and concise, so I'm publishing it here as an official guide.
Thanks again Ryan

If you don't have macports installed, don't install it. It'll make building other things a bit more tricky, as macports tends to compile for x86_64, rather than x86_64/i386.

Anyway, follow the instructions here to get RVM installed: https://rvm.io/rvm/install/ … You'll want to do a single-user install, which means that everything will be installed and running from within your home directory.

After you logout/login, you should be able to run `rvm info` and it won't give you errors. If that doesn't work, then you need to make sure that you've follow the part of the install that talks about putting stuff into your bash profile or rc file.

Here's what I did to get a BeEF environment going using rvm on my macbook (running 10.6.8):

`rvm install ruby-1.9.3`  - This installs ruby-1.9.3. I had issues when it tried to build using clang, but switching it to gcc worked. I don't know for certain if this will work under 10.7 :-/

`rvm use ruby-1.9.3` - Sets the rvm environment to use ruby-1.9.3 .. Yes, you can have multiple versions of ruby installed in completely separate environments. This is reason #1 why RVM rules.

At this point, you're working in a pristine environment specifically crafted for BeEF. All the gems that you install will only exist within this environment. Bundler comes installed with RVM, already.

To set up BeEF:

`git clone git://github.com/beefproject/beef.git beef`

`cd beef`

`rvm use ruby-1.9.3-p125@beef --create --ruby-version`  -- This creates an empty set of gems just for beef, it also makes it so that any time you switch into the 'beef' directory, rvm automatically switches to the appropriate environment.

`bundle install` - Bundler takes care of installing all of your dependencies.

`rvmsudo ./beef`  - Start up beef. Normally sudo will strip your environment out, rvmsudo will maintain your rvm environment.
If you run into goofy errors while trying to install ruby or any of the gems, it's likely because of macports.. Like I said, I've moved away from macports as it tends to stomp on my dev environment quite a bit. RVM is a real life-saver, to be honest.  I can install all the versions of ruby that are out there, while still keep them completely isolated from one-another.