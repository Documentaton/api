#Server role : Sphinx

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
