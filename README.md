# citADel

This project is an attempt to leverage Ansible to stand up a fresh RaspberryPi running PiHole, Unbound, and DNSMasq for use within my home network/lab.
The idea is to make it easily repeatable while also learning my way around Ansible.

Long term goals include:
* Incorporating other Infrastructure as Code tools, e.g. Packer for building the image, Terraform to allow deploying on multiple providers, etc.
* Create a means to deploy a stack to e.g. AWS, GCP, DigitalOcean to allow a one button/command means of building an ad-blocking dns service in various regions for travelling.
* Bake in OpenVPN or similar for an added layer of protection -- either so I can VPN back to my home network or anonymize my traffic to an end point of my choosing to add a bit of protection when on public wifi, for example.

## Requirements
* A RaspberryPi
* A clean install of Raspbian Lite flashed to the (micro)SD card that will go in the RasPi (see ApplePi-Baker and/or balenaEtcher to flash with MacOS, use `dd`)
* After flashing Raspbian onto the card, `touch /boot/ssh` to enable SSHd on boot, which is needed for a headless install
* An SSH keypair to use for passwordless SSH access to the device.
* Ansible installed on your local system

## Process
1. Insert SD carn in RasPi and boot up.
1. Use nmap or dhcp logs to find its IP address.
1. Edit the hosts.example file, adding your RasPi IP under the `[pihole]` section
1. Verify that you can SSH to it with the default `pi:raspberry` credentials.
1. `mkdir ~/.ssh && touch ~/.ssh/authorized_keys`
1. `vi ~/.ssh/authorized_keys` and copy/paste your id_rsa.pub contents. Write and exit.
1. 

## TODOs:
* Automate the ssh key config/copy via a Makefile or some other way
* Find a way to give different nodes different hostnames (first block of main.yml)
* Could I use a Makefile to make the initial (pre-Ansible) setup and config more frictionless? Would that be dumb/redundant?
  1. Take desired/expected IP as input
  1. Create/update the `hosts` file in the repo
  1. SCP id_rsa.pub for ansible/pi user to authorized_keys
  1. Invoke the Ansible playbook/run
* 

## Other Notes
* Once everything's setup, you'll probably want to find the MAC of your Pi and give it a reserved IP on your router/dhcp server.
*

## Links, References, and Inspiration

* [balenaEtcher](https://www.balena.io/etcher/)
* [ApplePi-Baker v2](https://www.tweaking4all.com/hardware/raspberry-pi/applepi-baker-v2/)
* [Raspian Download](https://www.raspberrypi.org/downloads/raspbian/)

* [Complete Guite to Set Up Raspberry Pi Without a Keyboard and Mouse](https://sendgrid.com/blog/complete-guide-set-raspberry-pi-without-keyboard-mouse/)
*
