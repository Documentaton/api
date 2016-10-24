#Server role : Sphinx

In a standard OnPrem® deploy we will install two Sphinx nodes for redundancy.


###Installation Steps:

Install essentials packages for sphinx Server
Executes /opt/kaltura/bin/kaltura-sphinx-config.sh /root/ansible-kaltura.ans
Copies template to /opt/kaltura/app/configurations/sphinx/populate/{{ ansible_hostname }}.ini
Copies populate init files to sphinx servers
Multiple sphinx optimizations & config changes
Sphinx services are restarted

###Role:
Kaltura-sphnx playbook:

###Hosts:
[db]
Vault parameters in use:

###Sphinx Params
primarysphinx: 
secondarysphinx: 

###Note:

[ansible_hostname](https://github.com/Kaltura-PS/onprem-ansible/blob/master/roles/kaltura-sphinx/templates/hostname.template.ini.j2) value arrives from ansible gathered facts (specifies same node hostaname)
