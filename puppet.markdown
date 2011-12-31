Puppet Notes
===============================

Setup Puppet 
--------------------------
### Prerequisite
puppet-master version >= puppet-agent version
**************************

### Steps
Install puppet using ruby gem package manager  
**************************

### Configuration
1. puppet client get cert from puppet master  
puppet-client> sudo puppet agent --server puppet.master.host --waitforcert 60 --test  
--server		puppet master server  
--waitforcert	wait for certification   
--test			run in front

1. puppet master sign  
puppet-master> sudo puppet cert --list  
puppet-master> sudo puppet cert --list --all  
puppet-master> sudo puppet cert --sign puppet.client.host

1. create site.pp on puppet master  
puppet-master> sudo vi /etc/puppet/manifests/site.pp

1. test on master  
puppet-master> sudo puppet apply site.pp

1. config client  
config file location /etc/puppet/puppet.conf  
puppet.client> sudo puppet agent --genconfig > puppet.conf  
NOTE: under [agent] section, find server = puppet, change the puppet to the master address
