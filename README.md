install_certbot_ssl_certs
=========================

This Ansible role will use the previously installed certbot binary to request Let's Encrypt SSL certificates for one or more sites on your webserver

Requirements
------------

Right now this setup only supports the Nginx webserver, but I'll be adding support for Apache soon.

Role Variables
--------------

(Required) The email of the Administrator

```
    install_certbot_ssl_certs_certbot_email: "admin@example.com"
```

The FQDN of the website you want a SSL cert for * WITHOUT * a "www" subdomain prefixing it. 
This is required unless `install_certbot_ssl_certs_use_list` is set to true, in which case this variable will be ignored.

```
    install_certbot_ssl_certs_website_to_secure: "example.com"
```

List of databases and users to setup. Not needed unless the `install_certbot_ssl_certs_use_list` variable is set to true. Default is false.

```
    install_certbot_ssl_certs_list_to_setup:
      - {
          url: 'yourcoolsite.com',
          https: 'true'
        }
```

(Default) Will you be passing a list of databases and/or database users to setup?

```
    install_certbot_ssl_certs_use_list: false
```

(Default) Directory on target server to store certbot binary

```
    install_certbot_ssl_certs_certbot_binary_dir: /opt/certbot
```

Dependencies
------------

- stancel.certbot_install

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```
	- hosts: your_webserver
	  vars_files:
	    - vars/main.yml
	  roles:
	    - stancel.install_certbot_ssl_certs 
```

or just pass the variables in the playbook

```
	- hosts: your_webserver 
	  vars:
		install_certbot_ssl_certs_certbot_email: "admin@example.com"
		install_certbot_ssl_certs_website_to_secure: "example.com"
	  roles:
	    - stancel.install_certbot_ssl_certs
```

License
-------

GPLv3

Author Information
------------------

[Brad Stancel](https://github.com/stancel)