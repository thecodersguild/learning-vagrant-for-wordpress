#_From the Ground Up:_ Learning Vagrant for WordPress 

> **Written 2016-01-01 by [@mikeschinkel](http://twitter.com/mikeschinkel)**

Consensus among the more advanced WordPress developers is that currently **Vagrant is the preferred choice for setting up a local web server** for WordPress development. Better than MAMP, WAMP, ServerPress or anything else that is similar.

**Note:** This tutorial will be most helpful if you are running a Mac on OS X. Those on Linux may also find it similarly helpful but I have made **no attempt to address Vagrant running on Windows** so chances are good the tutorials will not all work for you.  Caveat Emptor!

##What is Vagrant?

Vagrant is a tool that does lot of things and has a lot of uses. But let us _**limit to what is relevant for local WordPress development**:_

> _Vagrant is a software tool for loading and managing [**_Virtual Machines_**](https://en.wikipedia.org/wiki/Virtual_machine) on your development computer by controlling a [**_Provider_**](https://docs.vagrantup.com/v2/providers/) such as Oracle's VirtualBox or VMWare Fusion. The virtual machine will run a Linux-based web & database server such as Apache or Nginx & MySQL or Maria to server your web projects from WordPress's source files stored on a local directory of your development computer._
><br><br>
> _In addition Vagrant [_**Provisions**_](https://docs.vagrantup.com/v2/provisioning/index.html) your virtual machine by running whatever scripts and/or tools needed to install and configure server software -- tools like [_**Puppet**_](https://puppetlabs.com/puppet/what-is-puppet) and [_**Chef**_](https://learn.chef.io/) -- and Vagrant can also run [_**Composer**_](https://getcomposer.org/) to download and configure your source code to make your virtual machine ready for your development._

###Key Basics about Vagrant
- Vagrant is **Open-Source**, 
- Vagrant is a **Command-Line Tool**, and
- Vagrant's actions are **Configured via a File** named `Vagrantfile`.

##"Easy" Options for Vagrant + WordPress
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

**Except the problem with using these when you are new to Vagrant is** you will mostly likely get stuck without the skills to troubleshoot just as an algebra student could not begin to pass an advanced calculus test. And you really don't want to be stuck up a creek without a paddle when you are on a deadline.  

###Better to Learn Vagrant from the Ground Up
Once you'd learn the fundamentals of Vagrant then is makes sense to revisit potentially using these _"easy"_ solutions. And once you start to get proficient with Vagrant you can study the `Vagrantfile` for any of the above options to learn how to handle more advanced configurations.

When you do become proficient with Vagrant and whichever provisioner you choose then some of the pre-built easy options might be a great choice. However by then you'll probably want the control of building the exact box you need anyway.

##Prerequisites

There are several things you need to have installed and/or have experience with before even trying to work with Vagrant. They include:

- [**Terminal/Bash Command Line**](http://blog.teamtreehouse.com/introduction-to-the-mac-os-x-command-line) - If you are uncomfortable using the Bash command line you need to be prepared for at least a crash course on Terminal in parallel to learning about Vagrant. [**Here is a good place to start**](http://blog.teamtreehouse.com/introduction-to-the-mac-os-x-command-line). Also [here](http://www.macdevcenter.com/pub/a/mac/2001/12/14/terminal_one.html).

- [**On GitHub and Comfortable with Git**](https://github.com/thecodersguild/learning-git-for-wordpress) - If you do not have an account on GitHub and are not familiar with using Git to version control your source code now is as good a time as any to start.  [**You can start here**](https://github.com/thecodersguild/learning-git-for-wordpress).

- [**VirtualBox**](https://www.virtualbox.org/wiki/Downloads) - This one is easy. You just need to download and install Oracle's open-source VirtualBox. [**You can download an installer here**](https://www.virtualbox.org/wiki/Downloads). Or better yet read our _"[_**Quick Start Installing VirtualBox on Mac OS X**_](https://github.com/thecodersguild/quick-start-installing-virtualbox-on-mac-os-x)"_.

- [**Homebrew**](http://brew.sh) - _**OPTIONAL**_ but highly recommended. It will make installing most of the software tools on Mac OS X many times easier, and provides diagnostic tools to help you maintain a worked development machine.  To learn more about Homebrew check out _"[_**Quick Start Using Homebrew on Mac OS X**_](https://github.com/thecodersguild/quick-start-using-homebrew-on-mac-os-x)."_

##More to come...


