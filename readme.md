#_From the Ground Up:_ 
#&nbsp;&nbsp;&nbsp;Learning Vagrant for WordPress 

Consensus among the more advanced WordPress developers is that currently **Vagrant is the preferred choice for setting up a local web server** for WordPress development. Better than MAMP, WAMP and anything else that is similar.

##What is Vagrant?

Vagrant is a tool that does lot of things and has a lot of uses. But let us _**limit to what is relevant for local WordPress development**:_

> _Vagrant allows you to load and manage a [**_Virtual Machine_**](https://en.wikipedia.org/wiki/Virtual_machine) on your development computer by controlling a [**_Provider_**](https://docs.vagrantup.com/v2/providers/) such as Oracle's VirtualBox or VMWare Fusion. The virtual machine will run a Linux-based web & database server such as Apache or Nginx & MySQL or Maria to server your web projects from WordPress's source files stored on a local directory of your development computer._
><br><br>
> _In addition Vagrant [_**Provisions**_](https://docs.vagrantup.com/v2/provisioning/index.html) your virtual machine by running whatever scripts and/or tools needed like [_**Puppet**_](https://puppetlabs.com/puppet/what-is-puppet) or [_**Chef**_](https://learn.chef.io/) to install and configure server software as well as to run [_**Composer**_](https://getcomposer.org/) for downloading and configuring your source code. you required to make your VM ready for your development work._

###Key Basics about Vagrant
- Vagrant is **Open-Source**, 
- Vagrant is a **Command-Line Tool**, and
- Vagrant's actions are **Configured via a File** named `Vagrantfile`.

##"Easy" Vagrant Options for WordPress
There are many _"easy"_ options to get started using Vagrant with WordPress. They include:

- [VCCW](http://vccw.cc)
- [Trellis](https://roots.io/trellis/)
- [Chassis](http://docs.chassis.io)
- [VagrantPress](https://github.com/vagrantpress)
- [VIP Quickstart](https://vip.wordpress.com/documentation/quickstart/)
- [WordPress Machine](https://github.com/audionerd/wordpress-machine)
- [WordPress Kickstart](https://github.com/jnettome/wordpress_kickstart)
- [WordPress Vagrant Boxes](https://github.com/tierra/wp-vagrant)
- [Varying Vagrant Vagrants](http://varyingvagrantvagrants.org)
- [Easy WordPress VMs with Vagrant and Ansible](https://github.com/jalefkowit/vagrant-ansible-wordpress)
- [WPLib Box](https://github.com/wplib/wplib-box/)

**Except the problem with using all of these** is -- _if you are not yet proficient with Vagrant_ -- you will mostly likely to get stuck without the skills to troubleshoot like an algebra student in advanced calculus final exam, especially if you are on a deadline.  

**Better to learn Vagrant from the ground up** and then you can revisit potentially using these _"easy"_ solutions.


###Key Basics about Vagrant
