F5 Application Services 3 (AS3) Install
=========

This role will install Declarative Onboarding using F5's API. First we determine tmos version and then if we have AS3 locally, if not the sha256 checksum is downloaded followed by the AS3 rpm file from [F5's Github site](https://github.com/F5Networks/f5-appsvcs-extension/releases). <br/> Once downloaded and validated via sha256 checksum. Now focus is put on the F5 to see if AS3 exists, upon a 404 return (no AS3 installation exists)<br>
the installation begins and is verified.  Optionally you can delete the downloaded files.

Requirements
------------

None

Role Variables
--------------

Variables needed for this role include:

* AS3 version tag
* AS3 RPM version number
* AS3 checksum file name
* F5 management IP Address
* F5 Administrator username
* F5 Administrator passowrd
* Path to roles directory

```
as3Tag: "v3.20.0"
as3RPM: "f5-appsvcs-3.20.0-3.noarch.rpm"
as3Sha: "{{ as3RPM +'.sha256'}}"

#this will pull from group adc and use the first ansible_host listed
f5_mgmt: "{{ hostvars[groups['adc'][0]]['ansible_host'] }}"

e_user: "admin"
e_pass: "secret"
roles_d: "."
provider:
  user: "{{ e_user }}"
  password: "{{ e_pass }}"
  server: "{{ f5_mgmt }}"
  validate_certs: no

```


Dependencies
------------

None

Example
----------------


```
- hosts: [adc]
  gather_facts: no
  connection: local

  roles:
    - f5_as3_install

```



License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
