Perlbrew
=========

This "perlbrew" role allow you to install perlbrew on CentOS | Debian | RedHat | SUSE | Ubuntu.

[Perlbrew](http://perlbrew.pl) is a admin-free perl installation management tool.

Requirements
------------

Ansible 2.4

Tested on
---------

Ansible 2.7.8

Role Variables
--------------

* "perlbrew_perl_version" is used to specify the default perl version. Note: This cannot be `latest`, but need to be something like `perl-5.26.1`. The default will be changed to the latest stable.
* "perlbrew_user" is used to specify which user on the remote system that will get perlbrew.
* "perlbrew_usethreads" must be set to `true` to build a Perl with thread support, default is `false`. This will also append the string "-threads" to `perlbrew_perl_version` if `perlbrew_as` is not given.
* "perlbrew_switch" is used to activate (`perlbrew switch`) the new perlbrew_perl_version right away, default is `true` (if `false` added lines in `.profile`/`.bashrc` will be commented).
* "perlbrew_as" name of the perlbrew namespace, default is `perlbrew_perl_version`.

Example config:

    ---
    perlbrew_perl_version: perl-5.28.1
    perlbrew_user: wwwrun
    perlbrew_switch: true
    perlbrew_as: myperl

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
        - role: perlbrew 
          perlbrew_user: wwwrun
          perlbrew_perl_version: perl-5.24.3
          perlbrew_usethreads: true


License
-------

BSD

Author Information
------------------

Original author: Jan Henning Thorsen - jhthorsen@cpan.org - http://thorsen.pm
Slightly modified by: Toby Broyles
SUSE support: Bernhard Graf (augensalat)
