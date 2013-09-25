Instruction on installing Plone for the Training
================================================

We rely on Vagrant to give the same development-environment to everyone.

You should do these steps before the training to find out if they work and to not clog up the wireless there. Mail us if you encounter any problem! Keep in mind that you need a fast internet-connection during the while process since you'll have to download a complete virtual machine (ubuntu) and several packages and updates.


Install VirtualBox
-------------------------

Vagrant depends on Oracle’s VirtualBox to create virtual environments. Here is a link directly to the download page: https://www.virtualbox.org/wiki/Downloads
Wir need VirtualBox 4.0.x, 4.1.x or 4.2.x.

Install and configure Vagrant
-----------------------------

Get the latest version from http://downloads.vagrantup.com for your operating system and install it.

Now your system has a command 'vagrant' that you can run in the terminal.

First create a directory where you want to to the training in

    $ mkdir training
    $ cd training

Download a clean virtual machine (Ubuntu 12.04 Precise Pangolin 32bit). It will be downloaded and made available to the vagrant-command as 'precise32'. It serves as a basis for your virtual machines and can be reused as often as you like.

    $ vagrant box add precise32 http://files.vagrantup.com/precise32.box

Setup Vagrant to automatically install the current guest-additions. You can choose to skip this step if you encounter any problems with it.

    $ vagrant plugin install vagrant-vbguest

Now extract the files from the attached zip-files into your training directory. It should now hold the file "Vagrantfile" and the directories "manifests/" and "puppet_modules/"

Start the VM that is configured in "Vagrantfile"

    $ vagrant up

This takes a very loooong time since it not only sets up the MV but also updates your VM, installs various packages needed for plone-development and runs the installer for Plone 4.3.2.

If you have the feeling that something has gone wrong and the installation has not finished correctly for some reason try the following command to repeat the process. This will only repeat steps that have not finished correctly:

    $ vagrant provision

You can try this multiple times to fix problems, e.g. if your network-connection was down and thus steps could not finish.

Once the provisioning-process is completed you can login to the now running virtual machine:

    $ vagnant ssh

If you use Windows you'll have to login via putty (Install putty and follow the instructions her: http://vagrantup.com/v1/docs/getting-started/ssh.html)

You are now logged in as the user vagrant in /home/vagrant. We'll do all steps of the training as this user.

We installed a Plone 4.3.2 for you in the folder /home/vagrant/training/zinstance. You can run it now and access it from the browser.

    $ cd training/zinstance
    $ ./bin/instance fg

You can now point your browser at http://localhost:8080 and see Plone. This works since the port 8080 is forwarded from the guest-system (the vagrant-ubuntu) to the host-system (your normal operating-system). Now create a new Plone-Site by clicking "Create a new Plone-Site". The username and the password are both "admin" (Never do this on a real site!!!).

If you have any problems or questions please mail us at team@starzel.de

You can also work on your own machine with your own python and Plone if you really want to but please-please-please make sure that you have a system that will work since we don't want to loose any time with installing.

See you!