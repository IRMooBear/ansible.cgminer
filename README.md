[![Build Status](https://travis-ci.com/IRMooBear/ansible.cgminer.svg?branch=master)](https://travis-ci.com/IRMooBear/ansible.cgminer)

Install CGMiner on RPI
=========

This role will compile CGMiner with GekkoScience custom driver on a Raspberry Pi for use with the 2Pac or NewPac USB ASIC miners.

The installed cgminer.service will run a persistent screen session under the pi user.  The screen session will not terminate if ssh is disconnected.

To view the session
```
screen -r cgminer
```
To detach from the screen without quitting cgminer service
```
CTRL + A + D
```

Variables
----------------
    compile_threads: "{{ ansible_processor_cores }}"
    
Number of threads to run during compile.    
    
    cgminer_additional_config: ""
    
Unused...
    
    cgminer_bitcoin_wallet: 18YuqAaQPc3nqK53iVV5eTZKoENcf5mKVi
    
Your bitcoin wallet address to use in the template generation.
    
    cgminer_worker_name: newpac
    
Mining working name.
    
    cgminer_gekko_2pac_freq: 125.0
    
2PAC frequency, must at as float with xx.0
    
    cgminer_gekko_start_freq: 100   
    cgminer_gekko_step_freq: 25
    cgminer_gekko_step_delay: 30
    
I don't know what these are used for.  Apparently doesn't work for stick miners.  
  
    cgminer_gekko_newpac_freq: 125
    
NewPac frequency, fun times with clock settings.
    
    cgminer_gekko_newpac_core: 400
    
Core setting, leave it alone.
    
    cgminer_suggest_difficulty: 512
    
Suggested difficulty to mining pool.
    
    cgminer_asic_boost: "true"
    
Turn on/off ASIC boost, must include quote.
    
    cgminer_autostart: no
    
Start CGMiner on system boot.
    
    cgminer_user: irmoobear
    cgminer_password: x
    
Your mining authentication.
    
    cgminer_git_version: 3339a51e136be269125a74ece852ae81201bd528
        
Git version to pull for compile.    
    
    cgminer_pools:
      -
        url: stratum+tcp://pool.ckpool.org:443
        user: "{{ cgminer_bitcoin_wallet }}.{{ cgminer_worker_name }}"
        pass: "{{ cgminer_password }}"
      -
        url: stratum+tcp://solo.ckpool.org:443
        user: "{{ cgminer_bitcoin_wallet }}.{{ cgminer_worker_name }}"
        pass: "{{ cgminer_password }}"
      -
        url: stratum+tcp://stratum.multipool.us:3360
        user: "{{ cgminer_user }}.{{ cgminer_worker_name }}"
        pass: "{{ cgminer_password }}"

Variable for the template to generate configuration file.  Customize with your own pool settings.

Example Playbook
----------------
1. Set authentications and pools first before running!

    - hosts: servers
      roles:
         - { role: irmoobear.install_cgminer }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
