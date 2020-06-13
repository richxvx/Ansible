# Configuration management with <u>Ansible</u>

For this project, I wanted to learn how I could automate certain tasks, such as updates, to other systems on my network. I decided to use Ansible.

Ansible is very simple to use. You setup Ansible on your main server (the *control node*), and your client machines (your *managed nodes*) only need to have SSH running; no other software is required.

## Installing Ansible

The installation of Ansible is very straightforward. Im using a Ubuntu server, so I used the command `sudo apt install ansible`

After running Ansible, we get various options:

<img title="" src="https://drive.google.com/uc?id=1uh0zpSBrDMGSBZfRHTGcBELgrbybkjNv" alt="" width="617">

## Using Ansible

Before we can send out commands to our host machines, we need to add the ip addresses of our hosts to the **<u>hosts</u>** file in `/etc/ansible/hosts`

<img title="" src="https://drive.google.com/uc?id=18KOGZMeRIPFonk5NUjJQ-1VJelTFzYZx" alt="" width="617">

I created a Linux group and added the ip addresses of the host machines I want to send commands to. I pinged my machnies with ansible to make sure everything was working properly.

<img title="" src="https://drive.google.com/uc?id=1xlYb5mSsi98K2zD3YvYm56MYZqh6gFmU" alt="" width="611">

It works! in the command `ansible linux -m ping` I specified my Linux group, and used -m to use the ping module. You can also run your own commands like this: `ansible linux -a 'ls'`

Time to take things one step further.

## Playbooks

Ansible refers to yaml files as **<u>playbooks</u>**, and within these yaml files, you can perform various tasks. I created a yaml file to update my linux systems.

<img title="" src="https://drive.google.com/uc?id=1b9TXYHU0b_GC9dER0COA-UHFE8iMG2Ud" alt="" width="618">

Now I can run `ansible-playbook updates.yml`; I recieved this output:

#### <img title="" src="https://drive.google.com/uc?id=1xqN687OdetdWPIqgpyuxfYrTrzT50hb2" alt="" width="613">

My host machines are now up to date.

## Conclusion

Ansible is a great and easy to use tool for configuration management that doesn't take long to setup. Once you're up and running, you can quickly get started automating tasks.
