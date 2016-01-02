#_From the Ground Up:_ Learning Vagrant for WordPress on Mac OS X

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

##Installing Vagrant
There is an easy way and a slightly less easy way to install Vagrant on Mac OS X. 

Choose your poison:

1. The easy way to install Vagrant is [**using HomeBrew with Caskroom**](https://github.com/thecodersguild/quick-start-using-homebrew-on-mac-os-x):

        $ brew cask install vagrant

2. The slightly less easy way is to [**download the Vagrant installer**](https://www.vagrantup.com/downloads.html), mount the disk image (`.DMG`) file, and then run the `Vagrant.pkg` installer.


##Choosing a Box 

Vagrant needs to start with a bootable disk image of your desired operating system which Vagrant vernacular is called a _"Box"_.  You could build your own Box if you wanted but there are literally hundreds available free for the taking, erm, the downloading. You can [**search or browse for boxes here**](https://atlas.hashicorp.com/boxes/search). 

One of the most downloaded boxed is `hashicorp/precise32` probably because [it is used for the example on the Vagrant home page](https://www.vagrantup.com/).

Another box to consider is [`scotch/box`](https://box.scotch.io/) which is a box with a simple LAMP stack installed.

Finally, consider [`wplib/wplib-box`](http://github.com/wplib/wplib-box) which provides everything you need for local development using the [**WPLib Professional Development Platform for WordPress**](http://wplib.org).

##Initializing your First Vagrantfile
Let us pick the **Precise32 Box** because it is the least likely to cause headaches when just getting started. 

Create a directory `~/Sites/vagrant-wp` and then initialize Vagrant there:

    $ mkdir ~/Sites/vagrant-wp
    $ cd ~/Sites/vagrant-wp
    $ vagrant init hashicorp/precise32

That last command generates the following `Vagrantfile` _(I removed comments that are generated to reveal just the actual commands. You'll note [_the Vagrant syntax is the Ruby language_](http://www.eatmybusiness.com/food/2015/07/13/learn-just-enough-ruby-syntax-to-understand-how-to-write-a-vagrantfile/296/)):_

    Vagrant.configure(2) do |config|
        config.vm.box = "hashicorp/precise32"
    end

**If you are curious to see the full `Vagrantfile` complete with generated comments** you can `cat` its contents to the terminal window:

    $ cat Vagrantfile | more
    
##Running your First Box via Vagrant
This step is simple. Just run:

    $ vagrant up
    
This will take at least a few minutes.  It will first check to see if you have the Precise32 Box downloading and if not it will download for you.

###If It Does Not Work?
Vagrant isn't magic and sometimes it does not work.  If you run into problems at any time, just to [**Troubleshooting Vagrant**](#troubleshooting-vagrant) for potential help.

###Where are Local Vagrant Boxes Stored?
When Vagrant downloads a box it places it in the `~/.vagrant.d/boxes` folder on Mac OS X. Why not open another Terminal window while `vagrant up` runs and check it out?:

    $ ls -l ~/.vagrant.d/boxes/
    
When you run that command you will probably get output something like this:

    drwxr-xr-x+ 4 mikeschinkel  staff  136 Jan  1 07:33 hashicorp-VAGRANTSLASH-precise32

###Downloading a Vagrant Box Directly _(OPTIONAL)_
While on the subject of boxes, Vagrant has the `box add` command that allows you to _**just**_ download a Box and place into your Box store at `~/.vagrant.d/boxes` for later use.  

Let's downloading the [**Scotch Box**](https://box.scotch.io/) directly in your other Terminal window:

    $ vagrant box add scotch/box

After downloading if you run `ls -l ~/.vagrant.d/boxes/` you should see something like:
    
    drwxr-xr-x+ 4 mikeschinkel  staff  136 Jan  1 07:33 hashicorp-VAGRANTSLASH-precise32
    drwxr-xr-x+ 4 mikeschinkel  staff  136 Jan  2 02:51 scotch-VAGRANTSLASH-box


##Access Your Vagrant Box's Command Line
Once your Vagrant Box is up and running you can connect directly to is and access it's command line using **SSH**:

    $ vagrant ssh

Go ahead, look around in your new Vagrant box.  Do an `ls` on the special `/vagrant` directory:

    (box) $ ls /vagrant
    
### Vagrant Mirrors Files Between Virtual Box and Local Computer 
The `/vagrant` directory inside your virtual box is a _mirror_ of your local computer's `~/Sites/vagrant-wp` directory where you have created the `Vagrantfile`. _**THIS**_ is the key magic that makes Vagrant so great for web development; it lets you edit your files locally yet serve them to your browser via your virtual box!

Let's use `echo` to create an `index.html` file, still from within your virtual box:

    (box) $ echo Hello World! > /vagrant/index.html
    
Now type `exit` to exit the virtual box and _Shazam!_ you will find your new `index.html` in the same folder as your `Vagrantfile` on your local computer.  

## Installing a Web Server
We'll install Apache because it's the most widely known. This requires us to run a [**provisioning script**](https://docs.vagrantup.com/v2/provisioning/shell.html).  **Add the following** to your `VagrantFile` just after the `config.vm.box` assignment:

    config.vm.provision :shell, path: "provision.sh"
    
That command tells Vagrant to run a provisioning script on the virtual machine when you run `vagrant up` for the first time, or `vagrant reload --provision` after your first `vagrant up`.

###The Provisioning Script

**Create** `provision.sh` in the same folder as your `Vagrantfile`. It should contain the following [Bash shell script commands](http://www.panix.com/~elflord/unix/bash-tute.html):
 
    #!/usr/bin/env bash
    echo Installing Apache...
    apt-get update
    apt-get install -y apache2
    if ! [ -L /var/www ]; then
      rm -rf /var/www
      ln -fs /vagrant /var/www
    fi
    echo Apache Installed.
    
Explaining the script is a bit out of scope for now. If you'd like to learn more you can find details here:

- [Ubuntu's apt-get command](https://help.ubuntu.com/12.04/serverguide/apt-get.html)
- [Ubuntu's Apache installation](https://help.ubuntu.com/lts/serverguide/httpd.html)
- [Ubuntu's Beginner Bash Scripting](https://help.ubuntu.com/community/Beginners/BashScripting)
- [How to Check if a Directory Exists in a Bash Script](http://www.cyberciti.biz/faq/howto-check-if-a-directory-exists-in-a-bash-shellscript/)

###Reload and (Re-)Provision
Since we've made configuration changes we need to reload with the (re-)provision switch:

    $ vagrant reload --provision
    
This will take a bit of time like the original `vagrant up` did.
   
###Confirming Apache is Installed
Now we can test to see if Apache is installed with `apachectl`:

	$ vagrant ssh
    (box) $ apachectl -V
    
Apachectl should spit out a bunch of configuration lines if it is installed.
   
Then we can actually verify that Apache is serving web pages by running `wget` on our localhost _(that switch is "dash-uppercase-oh" followed by "space-dash-space"):_

    (box) wget -O - http://127.0.0.1
    
It all installed correctly then your `wget` call will have outputted your earlier echoed `Hello World!` content.

##Giving your Box an IP Address
You now have a web server on your box but no way to reach it from outside the box; we need to provide an IP address.  Add the following right after your `config.vm.provision` command _(we chose `99.99.99.99` because it is easy to remember!):_

    config.vm.network "private_network", ip: "99.99.99.99"

Then reload and re-provision:

    $ vagrant reload --provision
    
Now you should be able to make requests of your virtual box's Apache server from your local computer. Try this _(that switch is "dash-zero"):_

    $ curl -0 http://99.99.99.99/
    
If `curl` output `Hello World!` you have success! Next try `http://99.99.99.99/` in your favorite browser and you should get the same result.



##%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

##Troubleshooting Vagrant
Sometimes Vagrant can be infuriating. It's often hard to debug a problem, but here are some of the problems we've run into and the solutions we discovered:

###Breaking out of a Running Vagrant Script

For example, you might get the following output repeatedly:

    default: Warning: Remote connection disconnect. Retrying...

The first thing to try is to wait to see if your system is just responding slowly.

But if you are tired of waiting you can press `Ctrl-Z` (no, not `Cmd-Z`) to break out of the loop. You may need to press it a few times to break out completely and get a command prompt back.

Once you break out you may need to kill Ruby since it is likely still running. You can run Activity Monitor

###Turn on the GUI
Sometimes your _"headless"_ box will be waiting for a user to do something and with the GUI turned off you'll never know.  The following will turn on the GUI so you can see if your box is waiting for any kind of input.

Uncomment the following lines in your `Vagrantfile` generated by `vagrant init`, or add them if you are writing the file from scratch:

    config.vm.provider "virtualbox" do |vb|
       vb.gui = true
    end

If you are writing your `Vagrantfile` from scratch be sure to include them inside the following control structure:

    Vagrant.configure(2) do |config| 
        config.vm.box = scotch/box"
        config.vm.provider "virtualbox" do |vb|
            vb.gui = true
        end
    end 

Now run `vagrant up` again and see if that reveals an issue you can resolve.

###When the GUI Captures your Mouse
If you are looking at the VirtualBox window and you seem to loose your mouse cursor, VirtualBox will _"release"_ it when your press `Left-Cmd` (or it may be another key; look at the bottom right corner of the _"[_window chrome_](https://www.nngroup.com/articles/browser-and-gui-chrome/)"_ for your VirtualBox window.


###Google is your Friend
And if none of the above helps then Google may be your friend here. 

If you get an error message google it along with "Vagrant" and removing anything that's unique to your machine in the error message such as directory names.
