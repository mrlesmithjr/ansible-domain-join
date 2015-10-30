Role Name
=========

Installs and configures PBIS-Open and auto joins domain...http://download1.beyondtrust.com/Technical-Support/Downloads/PowerBroker-Identity-Services-Open-Edition/

Requirements
------------

##### Domain Information - Required
###### Domain Name - example.org
###### Domain Netbios Name - EXAMPLE
###### Domain OU - Ansible
###### Domain User - ansible (account w/privileges to join domain or delegation)
###### Domain Password - xxxxxxx

Role Variables
--------------

````
---
# defaults file for ansible-domain-join
ad_domain: '{{ pri_domain_name }}'  #define your active directory domain - FQDN - same as pri_domain_name?
ad_domain_netbios: EXAMPLE   # enter NETBIOS name...ex...example.org = EXAMPLE
ad_ou: Ansible  #define active directory OU to place computer accounts
ad_password: [] # enter your domain user account password to join AD --- Better to prompt for this in playbook
ad_user: [] # enter your domain user account to join AD --- Better to prompt for this in playbook
pbis_debian_download: '{{ pbis_debian_file }}.sh'
#pbis_debian_file: pbis-open-8.2.2.2993.linux.x86_64.deb
pbis_debian_file: pbis-open-8.3.0.3287.linux.x86_64.deb
#pbis_debian_url: http://download.beyondtrust.com/PBISO/8.2.2/linux.deb.x64
pbis_debian_url: http://download.beyondtrust.com/PBISO/8.3
pbis_dl_dir: /opt  #defines where PBIS will be downloaded to and executed from
sudo_ad_group_name: '\Domain^Admins ALL=(ALL) ALL'
sudo_ad_group: '{{ sudo_ad_name }}{{ sudo_ad_group_name }}'
sudo_ad_name: '%{{ ad_domain_netbios }}\'
sudoers_filename: '{{ ad_domain }}_domain_users'

#### Download locations
# http://download.beyondtrust.com/PBISO/8.3/pbis-open-8.3.0.3287.linux.x86_64.deb.sh
# http://download.beyondtrust.com/PBISO/8.2.2/linux.deb.x64/pbis-open-8.2.2.2993.linux.x86_64.deb.sh
````

Dependencies
------------

None

Example Playbook
----------------
#### Galaxy
-----------
    - hosts: servers
      roles:
         - { role: mrlesmithjr.domain-join }
#### GitHub
-----------
    - hosts: servers
      roles:
        - ansible-domain-join

License
-------

BSD

Author Information
------------------

Larry Smith Jr.
- @mrlesmithjr
- http://everythingshouldbevirtual.com
- mrlesmithjr [at] gmail.com
