## Vagrantfile for MongoDb Development Server on Ubuntu

### Introduction
This is a Vagrant file (and .zshrc template) for a Vagrantbox designed specifically to provide a MongoDb installation and web-based administration (through mongo-express):

The base box that has been used is by the lovely folk at boxcutter (https://vagrantcloud.com/box-cutter) who make boxes that works across the various vagrant providers - primarily:
* Oracle's VirtualBox (the default for Vagrant)
* Parallels (get the plugin here https://github.com/Parallels/vagrant-parallels)
* VMWare (you will need a paid plugin for VMWare and Vagrant)

### Current Features

 * Ubuntu 14.04 LTS
 * MongoDb (Latest Stable)
 * nodejs and npm
 
### Instructions

* Clone Repo
```
git clone https://github.com/shabbirh/VagrantMongo.git
```
* Goto the folder you've cloned the repo to.
* Tear up vagrant
```
vagrant up
```
* The first time you provision the machine may take a longer as a number of archives need to be downloaded.  Following that - as long as you don't destroy the machine - everything should be fast.

* You can then use a Mongo Client such as RoboMongo or MongoChef to work with your MongoDb.  

### Note
This vagrant file has been tested across the following operating systems and virtualization environments:

* Windows 8.x and 10 with VirtualBox
* Mac OSX 10.11 with Parallels
* Mac OSX 10.11 with VirtualBox