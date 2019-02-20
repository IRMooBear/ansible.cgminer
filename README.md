[![Build Status](https://travis-ci.com/IRMooBear/pi-install-cgminer.svg?branch=master)](https://travis-ci.com/IRMooBear/pi-install-cgminer)

Pi Install CGMiner
=========

This role will compile cgminer with GekkoScience custom driver on a Raspberry Pi for use with the 2Pac or NewPac USB ASIC miners.

The install cgminer.service will run a persistent screen session under the pi user.  The screen session will not terminate if ssh is disconnected.

To view the session
```
screen -r cgminer
```
To detach from the screen without quitting cgminer service
```
CTRL + A + D
```
Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: irmoobear.pi_install_cgminer }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
