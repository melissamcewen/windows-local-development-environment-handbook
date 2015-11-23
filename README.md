# Local Development Environment On Windows Handbook
It all started one day when I got a new job and they handed me a Windows computer. For the past 9 years I'd mainly been developing on Linux and Mac, so I was a bit apprehensive. This handbook is a hopefully a useful document, but also a record of my attempts. So far it honestly hasn't been going well. I feel like I'm spending more time on my development environment than on developing. I've developed a healthy hatred for Windows file systems. 

# Goals
Well I do basically everything. I'll full stack. I work on PHP, Javascript (Angular and Node) mostly, some Ruby on Rails. I do a ton of Drupal projects. I'd like my local development environment to be portable, fast and you know, actually work.

# The Story So Far
I started out with this [Vagrant LAMP](https://github.com/r8/vagrant-lamp), accessed via Putty. It seemed to be going OK, but it was slower than molasses. So someone on Stack Exchange or something told me nfs was a good solution. I switched to nfs and everything was so awesome and fast. I was so happy. I was mostly working on Drupal projects.

Until the day I had some node.js and ruby stuff to do. All the sudden it was like every thing possible to go wrong went wrong. [This article](http://perrymitchell.net/article/npm-symlinks-through-vagrant-windows/) pretty much sums it up and recommends not using Windows (lol). I did some tricks and got things to work sometimes by doing crazy hacks like installing my node projects into my non-shared environment and putting them also in my shared folder but changing the execution path.  Blah blah, not very functional or sustainable. 

So I found out rsync was a cool alternative to nfs, but Vagrant Up was like "hey we can't do this on normal Windows CMD because we don't know anything about anything." So in order to try that I installed Cygwin and installed it at least five other times because I didn't realize I needed to select things like SSH. Unfortunately it still didn't work very well. Right now I'm trying the newer [smb](https://docs.vagrantup.com/v2/synced-folders/smb.html) option and though it's a pain to mount, it's performing pretty fast and not breaking anything...at least that I know of yet.

# Current thingamajig setup stuff

* this [Vagrant LAMP](https://github.com/r8/vagrant-lamp)
* Windows Whatever, the one with the tiles stuff. 
* like five million things like Cygwin and Putty

# Issues
* [Cygwin + rsync clusterfuck](https://github.com/mitchellh/vagrant/issues/4073)
* [Compass doesn't work correctly](http://stackoverflow.com/questions/20531194/compass-watch-does-not-regenerate-css-inside-vagrant)
