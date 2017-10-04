Getting started
===============
Internet-in-a-Box runs on various GNU/Linux operating systems such as Fedora, Ubuntu, Debian, CentOS and Raspbian.

You can install Internet-in-a-Box on most late model desktop and laptop computers. It also supports Intel NUC, Intel Gigabyte BRIX, OLPC XO-1.5, XO-1.75, XO-4, Raspberry Pi 2 and Raspberry Pi 3. A VirtualBox VM can also used for testing purposes. Using Docker containers however is not recommended as our Ansible provisioning system requires low-level access to the operating system.

Please refer to [platforms](https://github.com/iiab/iiab/wiki/IIAB-Platforms) page for more information.

Internet-in-a-Box uses [Ansible](https://www.ansible.com/) infrastructure automation tool to deploy and configure all software packages. Ansible uses [Playbooks](http://docs.ansible.com/ansible/latest/playbooks.html) a human readable instruction files in YAML format. The Playbooks are divided into hosts, roles and tasks. 

````
├── roles
│   ├── 1-prep
│   │   ├─ defaults
|   |   |    ├──main.yml (lowest precedence variable definitions, overridden by <repo_root>/vars/default_vars.yml, overridden by ./vars/local_vars.yml.
│   │   ├── README.rst
│   │   ├── tasks
|   |   |    ├──main.yml (specifies the actions to install this role
│   │   └── templates
|   |   |    ├<(text files where ansible variables are substituted, specified via {% <variable> %} containers-(jinja2 language).
│   ├── 2-common
│   │   ├── README.rst
│   │   ├── tasks
│   │   └── templates

````

At runtime, Ansible gathers system information and makes it available (called 'facts') and combines this with  playbook defined 'variables' to guide the installation process. The execution follows a sequence of cascading steps:
     1. Bash script ./runansible follows instructions in "iiab.yml" in the root directory.
     2. Iiab.yml calls 9 aggregate roles (the numbered directories under ./roles/).
     3. Each aggregate role has a <role>/meta/main.yml which calls the individual named roles.

Please refer to [architecture](https://github.com/iiab/iiab/wiki/IIAB-Architecture) and [variables]( https://github.com/iiab/iiab/wiki/IIAB-Variables) page for more information.

Installation
============

Before you start the installation please refer to the [hardware section of FAQ](http://wiki.laptop.org/go/IIAB/FAQ#What_hardware_should_I_use.3F) page for memory, storage and network requirements for your platform. Also note that downloading content might take a long time on slower Internet connections.

If you are a developer, please consider [building Internet-in-a-Box from scratch](https://github.com/iiab/iiab/wiki/IIAB-Installation#do-everything-from-scratch).

Please refer to [Installation](https://github.com/iiab/iiab/wiki/IIAB-Installation) page for more information.

Debugging
=========

Here are few strategies for debugging problems during the Internet-in-a-Box installation.

* When a installation task fails, Ansible halts printing out a descriptive error message to the screen. This error information is also written to 'iiab-install.log' file within /opt/iiab/iiab. (Look through logs to check if preceding line ? contains the error).
* When an installation succeeds, the last lines printed on the screen will look like the following (failed=0):
    PLAY RECAP *********************************************************************
127.0.0.1                  : ok=405  changed=125  unreachable=0    failed=0   

* Search through the Ansible Playbooks using 'egrep -rn <string from the failing step> /opt/iiab/iiab/roles/*>' to find the failed task.
* You can add additional `debug print statements <http://docs.ansible.com/ansible/latest/debug_module.html>`__ to Ansible Playbooks for debugging the problem.
* Talk to us or report a bug using the information below.

 Please refer to [Ansible Playbook documentation](http://docs.ansible.com/ansible/latest/playbooks.html) for more information.

Reporting Bugs
==============

You can file bug reports on [GitHub](https://github.com/):

* Sign up for a [GitHub](https://github.com/) account
* Go to the [issue tracker on GitHub](https://github.com/iiab/iiab/issues)
* Search for existing issues using the search field
* If you don't find any similar issues, file a new issue!

Please consider providing a descriptive title, your OS information, error messages and steps to reproduce the issue.

Get in touch
============

* Join our [technology](http://lists.laptop.org/listinfo/server-devel) and [learning design](https://groups.google.com/group/unleashkids) mailing lists
* Join our [live calls](http://minutes.iiab.io) most Mondays and Thursday
* Join us on IRC live chat: [#schoolserver](https://webchat.freenode.net/?channels=#schoolserver) on [freenode]( https://www.freenode.net/)
* Post an idea or question to our [community forums](http://iiab.io/)
* Read our [Frequently Asked Questions (FAQ)](http://FAQ.iiab.io)