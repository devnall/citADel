# citADel

This project is an attempt to leverage Ansible to stand up a fresh RaspberryPi running PiHole, Unbound, and DNSMasq for use within my home network/lab.
This idea is to make it easily repeatable while also learning my way around Ansible.

Long term goals include:
* Incorporating other Infrastructure as Code tools, e.g. Packer for building the image, Terraform to allow deploying on multiple providers, etc.
* Create a means to deploy a stack to e.g. AWS, GCP, DigitalOcean to allow a one button/command means of building an ad-blocking dns service in various regions for travelling.
* Bake in OpenVPN or similar for an added layer of protection -- either so I can VPN back to my home network or anonymize my traffic to an end point of my choosing to add a bit of protection when on public wifi, for example.

## Requirements
* A RaspberryPi with built-in wifi (i.e. RasPi 3 or newer)
* A clean install of Raspbian Lite flashed to the (micro)SD card that will go in the RasPi (see ApplePi-Baker and/or balenaEtcher(MacOS))
* After flashing Raspbian onto the card, `touch /ssh` to enable SSHd on boot, which is needed for a headless install
* An SSH keypair to use for passwordless SSH access to the device.

## Process
1. Insert SD carn in RasPi and boot up.
1. Use nmap or dhcp logs to find its IP address.
1. Verify that you can SSH to it with the default `pi:raspberry` credentials.
1. `mkdir ~/.ssh && touch ~/.ssh/authorized_keys`
1. `vi ~/.ssh/authorized_keys` and copy/paste your id_rsa.pub contents. Write and exit.
1. 

## Links and References
* [balenaEtcher](https://www.balena.io/etcher/)
* [ApplePi-Baker v2](https://www.tweaking4all.com/hardware/raspberry-pi/applepi-baker-v2/)
* [Raspian Download](https://www.raspberrypi.org/downloads/raspbian/)
