Server role : Sphinx

In a standard OnPrem® deploy we will install two Sphinx nodes for redundancy.

Kaltura-sphnx playbook:

Installation Steps:

Install essentials packages for sphinx Server
Executes /opt/kaltura/bin/kaltura-sphinx-config.sh /root/ansible-kaltura.ans
Copies template to /opt/kaltura/app/configurations/sphinx/populate/{{ ansible_hostname }}.ini
Copies populate init files to sphinx servers
Multiple sphinx optimizations & config changes
Sphinx services are restarted

Hosts
[db]
Vault parameters in use:

# Sphinx Params
primarysphinx: 
secondarysphinx: 


Note:
parameter ansible_hostanme is used a variable from ansible gathered facts (same node hostname)
[I'm an inline-style link](https://www.google.com)
