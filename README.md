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

* Database
    * [MySQL] (#MySql)
* Search engine
    *  [Sphinx](#sphinx)
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


#MySql

In a standard OnPrem® deploy we will install MySQL MASTER-SLAVE replication. Only development enviroments such as "All in one" deployments will not have database redundancy.


## Installation 

### Steps
1. Install essentials for MySQL server
2. Create MySQL configuration from template (my.cnf.j2)
3. Remove binary log files to avoid restart issues
4. Security changes:
 * Delete anonymous user
 * Change root user password
5. Create Replication user for Master Slave Replication
6. Create Logrotate for MySQL

### Playbooks
  *	kaltura-mysql
  
### Roles
  *	kaltura-mysql-master  
  *	kaltura-mysql-slave
  
### Hosts
  *	[db]

### Vault parameters in use
* dbport
* dbrootuser
* dbrootpass 
* dbpass
* replpass
* dbhost
* dbmaster
* dbslave



## Notes:
> * (!) Always set a script to monitor MASTER-SLAVE sync
>  *	If the SLAVE lags behind the MASTER, you will see inconsistency in the platform, as writes are done on the MASTER but many reads are done on SLAVE
> * The failover switch to MySQL SLAVE is not automatic and requires human interventation


#Sphinx


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
