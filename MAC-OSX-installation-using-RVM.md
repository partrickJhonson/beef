A friend of mine (antisnatchor), Mike Ryan (@justfalter), wrote this amazing step-by-step guide on how to install BeEF on MacOSX using RVM.
It's very clear and concise, so I'm publishing it here as an official guide.
Thanks again Ryan

If you don't have macports installed, don't install it. It'll make building other things a bit more tricky, as macports tends to compile for x86_64, rather than x86_64/i386.

Anyway, follow the instructions here to get RVM installed: https://rvm.io/rvm/install/ … You'll want to do a single-user install, which means that everything will be installed and running from within your home directory. 

After you logout/login, you should be able to run `rvm info` and it won't give you errors. If that doesn't work, then you need to make sure that you've follow the part of the install that talks about putting stuff into your bash profile or rc file.

Here's what I did to get a BeEF environment going using rvm on my macbook (running 10.6.8):

`rvm pkg install readline`  - This installs the readline lib, which makes interactive ruby (irb) much more useful (ctrl-R for history, tab completion, etc). 

`rvm install ruby-1.9.3-p125 --with-readline-dir=$rvm_path/usr --with-gcc=gcc-4.2`  - This installs ruby-1.9.3-p125 with readline support. I had issues when it tried to build using clang, but switching it to gcc worked. I don't know for certain if this will work under 10.7 :-/

`rvm use ruby-1.9.3-p125` - Sets the rvm environment to use ruby-1.9.3-p125 .. Yes, you can have multiple versions of ruby installed in completely separate environments. This is reason #1 why RVM rules.

`rvm gemset create beef` - Creates a gemset specifically for BeEF. Read more here: https://rvm.io/gemsets/basics/ … This is reason #2 why RVM rules.

`rvm use ruby-1.9.3-p125@beef` - Switches to use the gemset we just created. 

At this point, you're working in a pristine environment specifically crafted for BeEF. All the gems that you install will only exist within this environment. Bundler comes installed with RVM, already. 

To set up BeEF:

`git clone git://github.com/beefproject/beef.git beef`

`cd beef`

`echo 'rvm use ruby-1.9.3-p125@beef' > .rvmrc`  -- This makes it so that any time you switch into the 'beef' directory, rvm automatically switches to the appropriate environment. It may prompt you with a big scary message the first time you switch to the dir. Just answer 'yes'.

`bundle install` - Bundler takes care of installing all of your dependencies. 

`rvmsudo ./beef`  - Start up beef. Normally sudo will strip your environment out, rvmsudo will maintain your rvm environment. 
If you run into goofy errors while trying to install ruby or any of the gems, it's likely because of macports.. Like I said, I've moved away from macports as it tends to stomp on my dev environment quite a bit. RVM is a real life-saver, to be honest.  I can install all the versions of ruby that are out there, while still keep them completely isolated from one-another. 