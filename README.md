# ![Kaltura](images/kaltura-logo.jpeg) + ![Ansible](images/ansible-logo.png) = ![NINJA](images/ninja.jpg)

# Kaltura OnPrem® install guide using Ansible

This guide will show you how to install OnPrem® using Ansible, as well providing details on the steps done by the playbooks and the server roles.

## Glossary

##### Getting started

* [Prerequisites](getting-started/)
* [Choosing a server for Ansible](getting-started/)
* [How are the Ansible scripts organized?](getting-started/)
* [Configuring Ansible vault file](getting-started/)
* [Setting up "/etc/ansible/hosts"](getting-started/)


##### Installing server roles

* [Database](server-roles/database/)
    * MySQL
* [Search engine](#sphinx)
    * Sphinx
* [Load Balancer and SSL terminator](server-roles/load-balancer/)
    * HAProxy
* [API](server-roles/API/)
    * Apache
* [DWH](server-roles/DWH/)
* [Batch](server-roles/batch/)
* [Admin](server-roles/admin/)
* [Streaming](server-roles/streaming/)
    * NGINX
* [LIVE](server-roles/live/)

##### Patches and extras
* Caching
* Backups
* Monitoring

























#Sphinx
#Server role : #Sphinx

In a standard OnPrem® deploy we will install two Sphinx nodes for redundancy.


###Installation Steps:

1. Install essentials packages for sphinx Server
2. Executes /opt/kaltura/bin/kaltura-sphinx-config.sh /root/ansible-kaltura.ans
3. Copies template to /opt/kaltura/app/configurations/sphinx/populate/{{ ansible_hostname }}.ini
4. Copies populate init files to sphinx servers
5. Multiple sphinx optimizations & config changes
6. Sphinx services are restarted

###Role:
Kaltura-sphnx playbook:

###Hosts:
[index]

###Vault parameters in use:

Sphinx Params
primarysphinx: 
secondarysphinx: 

###Note:

[ansible_hostname](https://github.com/Kaltura-PS/onprem-ansible/blob/master/roles/kaltura-sphinx/templates/hostname.template.ini.j2) value arrives from ansible gathered facts (Hostaname of the same node)
[#test] (fol/)
