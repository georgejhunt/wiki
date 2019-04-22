Configuration Variables
=======================

[Ansible](https://en.wikipedia.org/wiki/Ansible_(software)) and the IIAB playbooks use a sequence of operations and a set of conventions to define the variables of differing scope that govern a particular installation.

Facts
=====

When Ansible starts it gathers a long list of 'facts' about the host on which installation will take place.  It also allows the definition of a local_facts module that will run a script to gather any additional facts.

Variable Files
==============

The vars directory holds two files, default_vars.yml and local_vars.yml.  The former holds the default values for a number of global variables for the installation.  The latter allows deployments to override these values.  These parameters are either ones that a deployment may wish to override, such as iiab_domain, or global constants.

The initial local_vars.yml file comes from the git repo but is marked not tracked on the first run, so edits will not be lost, and is copied to /etc/iiab/[local_vars.yml](http://FAQ.IIAB.IO#What_is_local_vars.yml_and_how_do_I_customize_it.3F) where it may be edited.  Changes should not be made to [default_vars.yml](https://github.com/iiab/iiab/blob/master/vars/default_vars.yml) as they could be overwritten by a subsequent pull from the git repository.

Variables Set in the Admin Console
==================================

When installation is carried out using the [Admin Console](https://github.com/iiab/iiab-admin-console#admin-console-documentation) an additional variable file is populated, /etc/iiab/config_vars.yml, which is set via a graphical user interface.  Values in this file further override values in default_vars.yml and local_vars.yml files.  It should be kept in mind that the order of precedence of the variables files is that config_vars.yml overrides local_vars.yml, and local_vars.yml overrides default_vars.yml.  This is true whether the console is used to perform an install or one of the command line scripts.

Computed or Derived Variables
=============================

After Ansible has gathered its facts and loaded the variables files, it starts running roles in the order given in the top-level playbook.  For IIAB the first role is 1-prep. This role runs the local_facts module and then sets any variables that are derived from any of the above in computed_vars.yml.  For this reason the prep tag needs to be included any time an install is done using tags only.

Role Variables
==============

Ansible allows roles to have variables in a defaults/main.yml file in the role directory.  These variables have the lowest level of precedence and only take effect when no value was set anywhere else.  Our convention is to define variables in this file to softcode parameters and to make sure the variable will not be undefined if used elsewhere.  These may be thought of as role-specific constants.

Install and Enable
==================

Every role, except those that are dependencies of other roles, like mysql, has a global <role name>_install and a <role name>_enabled flag that determines if it is installed and if it is enabled.

Host and Domain
===============

The Host and Domain variables and their defaults are:

* iiab_hostname: box
* iiab_domain: lan

The host name defaults to box, but in the past was schoolserver because that is what OLPC XO laptops expected.

The domain name has a simple default and may be overridden in the Admin Console.

Variables in YML Files
======================

Ansible supports a set_fact command that can be used for variable assignment inside a particular yml file.  By convention these should only be local variables except for the use of this command in computed_vars.yml.

Use of Variables in Ansible Playbooks
=====================================

Here are the main playbooks stored in /opt/iiab/iiab:

* iiab.yml - used by ./runtags & ./runansible, with config_vars.yml
* iiab-base.yml - for ./install-support to install OpenVPN (idea: prior to installing IIAB)
* iiab-stages.yml - run by ./iiab-install (like iiab.yml but it adds roles/0-init/defaults/main.yml, and removes /etc/iiab/config_vars.yml)
* iiab-network.yml - run by ./iiab-network using config_vars.yml (just runs networking play)
* iiab-from-console.yml - run by Admin Console’s “Install Configured Options” using config_vars.yml
* [Tim Moody might generate others on-the-fly in future, then throw them away]

Context: ./runtags, ./runansible, ./install-support, ./iiab-install and ./iiab-network are all located in /opt/iiab/iiab

Related Settings Files in /etc/iiab
===================================

Some of the most critical IIAB settings are stored in these 8 files:

* [local_vars.yml](http://wiki.laptop.org/go/IIAB/local_vars.yml) - customize this file so that iiab-install correctly installs all your IIAB services/apps
* iiab.env - essential variables during installation; holds STAGE (counter) for iiab-install's 9 steps in iiab-stages.yml
* iiab.env.py, iiab.env.pyc - Python code/class to read iiab.env (basically exports WWWROOT == /library/www/html for iiab-refresh-wiki-docs, iiab-make-kiwix-lib)
* iiab.ini - tracks what’s been installed, in sequence, with dates (this state is recorded by ./runrole and ./iiab-install)
* config_vars.yml - null file must be “{}”, further populated by Admin Console’s “Save Configuration” button.  Used by iiab.yml & iiab-from-console.yml with vars/default_vars.yml & /etc/iiab/local_vars.yml
* uuid - used by OpenVPN, for future analytics "fieldback", currently not used on RPi Zero W ([#271](https://github.com/iiab/iiab/pull/271))
* openvpn_handle - human-readable machine identifier used by OpenVPN
* kiwix_catalog.json - downloaded from Kiwix.org when you click “Refresh Kiwix Catalog” in Admin Console

Order of Execution and Precedence
=================================

In order of execution, i.e. lowest precedence to highest:

* Get Ansible facts including [local facts](https://github.com/iiab/iiab/blob/master/scripts/local_facts.fact)
* Load any vars particular to [roles](https://github.com/iiab/iiab/tree/master/roles)
* Load [roles/0-init/defaults/main.yml](https://github.com/iiab/iiab/blob/master/roles/0-init/defaults/main.yml) ([iiab-stages.yml](https://github.com/iiab/iiab/blob/master/iiab-stages.yml) uses this one, BUT [run-one-role.yml](https://github.com/iiab/iiab/blob/master/run-one-role.yml) and [iiab-from-console.yml](https://github.com/iiab/iiab/blob/master/iiab-from-console.yml) do not)
* Load [default_vars.yml](https://github.com/iiab/iiab/blob/master/vars/default_vars.yml)
* Load OS-dependent variables i.e. [/opt/iiab/iiab/vars](https://github.com/iiab/iiab/tree/master/vars)/{{ ansible_local.local_facts.os_ver }}.yml
* Load [local_vars.yml](http://wiki.laptop.org/go/IIAB/local_vars.yml)
* Load config_vars.yml ([iiab-stages.yml](https://github.com/iiab/iiab/blob/master/iiab-stages.yml) doesn't use this one, BUT [run-one-role.yml](https://github.com/iiab/iiab/blob/master/run-one-role.yml) and [iiab-from-console.yml](https://github.com/iiab/iiab/blob/master/iiab-from-console.yml) do)
* <strike>Run computed_vars.yml (part of [0-init](https://github.com/iiab/iiab/tree/master/roles/0-init))</strike>
