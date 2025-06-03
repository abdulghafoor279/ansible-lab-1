ansible-lab-1
=============

.. contents::
   :local:

Introduction
------------

This repository contains a sample test lab designed to explore ansible and ansible awx functionality. It four Cisco routers where I will be trying different features.

Installation
------------

1. Install Python

   Open PowerShell as Administrator and run::

       bash
       sudo apt update
       sudo apt-get install python3
       sudo apt-get install python3-pip
       sudo apt-get install python3-venv

   Create a virtual enviroment and activate it::
    
       python -m venv MYVENV
       source MYVENV/bin/activate
    
   Ensure python and pip are installed correctly::

       python3 -V
       pip3 -V
       pip install --upgrade pip
       pip install --upgrade pip setuptools
       pip install ansible

2. Install AWX
	Follow the guide on this website: https://ansible.readthedocs.io/projects/awx-operator/en/latest/installation/basic-install.html

Useful Commands:
----------------

# Ensure you are in virtual environment:
source MYVENV/bin/activate

# Ensure your are at correct location to run ansible playbooks
cd "OneDrive - Sky"/scripting/ansible/opti-lab1

ansible-doc -l | grep cisco.ios.ios ---------------------- to ansible code samples
ansible-doc cisco.ios.ios_hostname ----------------------- Press "q" to come out

ansible -i hosts.yml
ansible -i hosts.yml routers
ansible -i hosts.yml routers -m ping
ansible -i hosts.yml routers -m ios_facts

ansible -i hosts.yml C8KV-1  -m cisco.ios.ios_command -a "commands='show ip int br'"
ansible -i hosts.yml all     -m cisco.ios.ios_command -a "commands='show cdp neighbors'"
ansible -i hosts.yml routers -m cisco.ios.ios_command -a "commands='show ip route eigrp'"

ansible-playbook -i hosts.yml 1_playbook_int_status.yml
ansible-playbook -i hosts.yml 2_playbook_save_config.yml
ansible-playbook -i hosts.yml 3_playbook_add_loopback.yml
ansible-playbook -i hosts.yml 4_playbook_remove_loopback.yml
ansible-playbook -i hosts.yml 5_playbook_config_int.yml
ansible-playbook -i hosts.yml 6_playbook_enable_cdp.yml
ansible-playbook -i hosts.yml 4_playbook_enable_eigrp.yml
