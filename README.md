# Local Development Environment On Windows Handbook
It all started one day when I got a new job and they handed me a Windows computer. For the past 9 years I'd mainly been developing on Linux and Mac, so I was a bit apprehensive. This handbook is a hopefully a useful document, but also a record of my attempts. So far it honestly hasn't been going well. I feel like I'm spending more time on my development environment than on developing. I've developed a healthy hatred for Windows file systems. 

# Goals
Well I do basically everything. I'll full stack. I work on PHP, Javascript (Angular and Node) mostly, some Ruby on Rails. I do a ton of Drupal projects. I'd like my local development environment to be portable, fast and you know, actually work.

# The Story So Far
I started out with this [Vagrant LAMP](https://github.com/r8/vagrant-lamp), accessed via Putty. It seemed to be going OK, but it was slower than molasses. So someone on Stack Exchange or something told me nfs was a good solution. I switched to nfs and everything was so awesome and fast. I was so happy. I was mostly working on Drupal projects.

Until the day I had some node.js and ruby stuff to do. All the sudden it was like every thing possible to go wrong went wrong. [This article](http://perrymitchell.net/article/npm-symlinks-through-vagrant-windows/) pretty much sums it up and recommends not using Windows (lol). I did some tricks and got things to work sometimes by doing crazy hacks like installing my node projects into my non-shared environment and putting them also in my shared folder but changing the execution path.  Blah blah, not very functional or sustainable. 

Using [wrk](https://github.com/wg/wrk) I've tested the various mount options


| Mount Type | Latency Ave | Req/Sec Avg | Pros                | Cons                                                          |
|------------|-------------|-------------|---------------------|---------------------------------------------------------------|
| Virtualbox | 15.42ms     | 325.80      | Things usually work | Occasional issues with Ruby                                   |
| NFS        | 3.52ms      | 1.61K       |                     | Node and Ruby seem to have issues                             |
| SMB        | 167.27ms    | 702.77      | Things usually work | Need to boot as admin from cmd, need to enter domain password |


# Current thingamajig setup stuff

* this [Vagrant LAMP](https://github.com/r8/vagrant-lamp)
* Windows Whatever, the one with the tiles stuff. 
* like five million things like Cygwin and Putty

# Issues
* [Cygwin + rsync clusterfuck](https://github.com/mitchellh/vagrant/issues/4073)
* [Compass doesn't work correctly](http://stackoverflow.com/questions/20531194/compass-watch-does-not-regenerate-css-inside-vagrant)
* [Errno::EPROTO: Protocol error - /vagrant/vendor /ruby](https://github.com/bundler/bundler/issues/3932) - with VB Mount
* Need to change default Chef recipe for MySQL my.cnf to increase max_allow_packet to 16777216
