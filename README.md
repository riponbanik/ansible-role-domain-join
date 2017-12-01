# domain_join
Automate Linux Machine join AD using Ansible. This module is inspired from the work of 
  * https://github.com/rahulinux/ansible-domain-join 
Domain Administrators  default group is configured to enable sudo 

## Requirements & Dependencies

### Ansible
It was tested on the following versions:
 * 2.4


### Operating systems

Tested with RHEL 7
Targeted for EL 

## Example Playbook

Clone the repository in the roles directory in ansible as install_snmpd and include this role in your list.
For example

```
- host: all
  vars_files:
    - vars/ad.yaml
  roles:
    - domain_join
```

## Variables

```
You need to privode the details to join linux into domain, like domain user who has right to add client into domain and DNS server and FQDNS.
Create ad.yaml file with the content below and include it into the plyabook. Make sure /etc/resolv.conf contains the dns server address
---
- ad_server:
    ip: xxxx
    fqdn: ad1.example.com
    user: svc_ad
    pass: 'xxxx'
    domain: example.com
```

## Testing 
```
sudo realm list
id __user_name__
ssh __user_name__@localhost
```

## Leaving the domain
If you want to reverse the process and remove yourself from the domain, simply run the ‘realm leave’ command followed by the domain name, as shown below. <br/>
realm leave example.com



