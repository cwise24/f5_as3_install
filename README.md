F5 Application Services 3 (AS3) Install
=========

This role will install Declarative Onboarding using F5's API. First we determine if we have DO locally, if not the sha256 checksum is downloaded followed by <br >
the AS3 rpm file from [F5's Github site](https://github.com/F5Networks/f5-appsvcs-extension/releases). Once downloaded and validated via sha256 checksum. Now focus is put on the F5 to see if AS3 exists, upon a 404 return (no AS3 installation exists)<br>
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
as3Tag: "v3.17.1"
as3RPM: "f5-appsvcs-3.17.1-1.noarch.rpm"
as3Sha: "f5-appsvcs-3.17.1-1.noarch.rpm.sha256"
f5_mgmt: "<IP address>"
f5_u_cred: "admin"
f5_u_pass: "secret"
roles_d: "/home/user/roles"

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

  vars_files:
    - var_file.yml

  roles:
    - f5_as3_install

```



License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
