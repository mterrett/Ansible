# Ansible Inventory File (hosts.ini)

The hosts.ini file is an inventory file that organises managed nodes alongside system information and network location in one or more centralised file. Using an inventory file allows for Ansible to manage a large number of hosts with a single command.

Inventory files can be split up into groups like the following:

```
[dev_azure_web_vms]
192.168.1.10
192.168.1.11
192.168.1.12
dev-azure-web001

[prd_azure_web_vms]
192.168.100.10
192.168.100.11
192.168.100.12
prd-azure-web001
```

Inventory files can be created in either .ini or .yaml format, .ini is simpler to read and quite straightforward so they are used with smaller inventory files. Larger inventory files are typically recommended to be created using the .yaml format, which will look the below:

```
dev_azure_web_vms:
  hosts:
    dev_server_01:
      ansible_host: 192.168.1.10
    dev_server_02:
      ansible_host: 192.168.1.11
    dev_server_03:
      ansible_host: 192.168.1.12
```

## Tips for building inventories

Inventory groups names should be meaningful and unique, group names are also case sensitive so consider that in any naming convetion.
Avoid using spaces, hyphens and numbers preceding the group name, for example in a sitation where groups are based off rack number don't use 1st-rack or 1st_rack, use rack_1.
Where possible name your hosts groups logically with:

### What 
Group hosts according to what they're, for example: *web* or *app* servers, *databases* etc.

### Where
Group hosts by geopgrahic location, for example: *datacenter* *region* *floor/building*

### When
Group hosts by when they appear in a DevOps stage (if applicable), for example: *development*, *quality assurance testing*, *staging*, *production*

## Meta Groups

Using the above is all fine and dandy until the very real use case that you need groups to manage entire layers of infrastructure, this is where *metagroups* come into play. 

A metagroup is a group that contains other groups, instead of individual hosts. For example, you may wish to automate tasks across web servers and app servers in the production environment. That could look like the following:

```
webservers:
  hosts:
    webserver01:
      ansible_host: 192.0.4.140
    webserver02:
      ansible_host: 192.0.4.150

appservers:
  hosts:
    appserver01:
      ansible_host: 192.0.4.140
    appserver02:
      ansible_host: 192.0.4.150

production_servers:
  children:
    webservers:
    appservers:
```

Groups can have subscriptions across multiple metagroups, for example, you wish to automate tasks/deployments to all web servers across the stages. Adopting what we did in the previous example, that would look like the following

```
production_webservers:
  hosts:
    webserver01:
      ansible_host: 192.0.4.140
    webserver02:
      ansible_host: 192.0.4.150

staging_webservers:
  hosts:
    webserver01:
      ansible_host: 192.0.3.140
    webserver02:
      ansible_host: 192.0.3.150

development_webservers:
  hosts:
    webserver01:
      ansible_host: 192.0.2.140
    webserver02:
      ansible_host: 192.0.2.150

production_appservers:
  hosts:
    appserver01:
      ansible_host: 192.0.4.140
    appserver02:
      ansible_host: 192.0.4.150

production_servers:
  children:
    production_webservers:
    production_appservers:

webservers:
  children:
    development_webservers:
    staging_webservers:
    production_webservers:
```

The example above demonstrates that the *production_servers* group belongs to both the overarching *webservers* metagroup and the *production_servers* metagroup. 