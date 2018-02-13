Getting started
===============
Internet-in-a-Box runs on various GNU/Linux operating systems such as Raspbian, Ubuntu, Debian, CentOS and Fedora.

You can install Internet-in-a-Box on most late model desktop and laptop computers. It can run on Intel NUC, Gigabyte BRIX, OLPC XO-1.5, XO-1.75, XO-4, Raspberry Pi 3, Raspberry Pi 2 and Raspberry Pi Zero W. A VirtualBox VM can also be used for testing purposes. Using Docker containers is not recommended however, as our Ansible provisioning system requires low-level access to the operating system.

Please refer to [IIAB Platforms](https://github.com/iiab/iiab/wiki/IIAB-Platforms) for more information.

Internet-in-a-Box uses [Ansible](https://www.ansible.com/) infrastructure automation tool to deploy and configure all software packages. Ansible uses [playbooks](http://docs.ansible.com/ansible/latest/playbooks.html) a human readable instruction files in YAML format. Playbooks are divided into hosts, roles and tasks.
```
├── roles
│   ├── 1-prep
│   │   ├─ defaults
|   |   |    ├──main.yml (variables defined at /opt/iiab/iiab/vars/default_vars.yml can be overridden by /opt/iiab/iiab/vars/local_vars.yml)
│   │   ├── README.rst
│   │   ├── tasks
|   |   |    ├──main.yml (actions that install this role)
│   │   └── templates
|   |   |    ├──(text files where Ansible variables are substituted, using jinja2 templating e.g. {% <variable> %})
│   ├── 2-common
│   │   ├── README.rst
│   │   ├── tasks
│   │   └── templates
```
Internet-in-a-Box installation begins with 0-init, followed by Stages 1 to 9, and finally the network stage:
- [0-init](https://github.com/iiab/iiab/tree/master/roles/0-init)
- [1-prep](https://github.com/iiab/iiab/tree/master/roles/1-prep)
- [2-common](https://github.com/iiab/iiab/tree/master/roles/2-common)
- [3-base-server](https://github.com/iiab/iiab/tree/master/roles/3-base-server)
- [4-server-options](https://github.com/iiab/iiab/tree/master/roles/4-server-options)
- [5-xo-services](https://github.com/iiab/iiab/tree/master/roles/5-xo-services)
- [6-generic-apps](https://github.com/iiab/iiab/tree/master/roles/6-generic-apps)
- [7-edu-apps](https://github.com/iiab/iiab/tree/master/roles/7-edu-apps)
- [8-mgmt-tools](https://github.com/iiab/iiab/tree/master/roles/8-mgmt-tools)
- [9-local-addons](https://github.com/iiab/iiab/tree/master/roles/9-local-addons)
- [network](https://github.com/iiab/iiab/tree/master/roles/network)

Click on Stages 1 to 9 above for descriptions of their specific purpose.

At runtime (when building up your Internet-in-a-Box server) Ansible gathers system information making it available (as 'facts') and combines this with Ansible 'variables' to guide the installation process. The execution follows a sequence of cascading steps:

1. Bash script `./iiab-install` (formerly `./runansible`) uses Ansible to run `/opt/iiab/iiab/iiab-stages.yml`

2. `iiab-stages.yml` calls 9+ aggregate roles (the numbered directories above, stored in /opt/iiab/iiab/roles).  Within the 9 core install stages, it avoids repetition after Internet glitches by keeping a counter (STAGE) in `/etc/iiab/iiab.env`

3. Each aggregate role has a `<role>/tasks/main.yml` (formerly `<role>/meta/main.yml`) to call the individual named roles.

Please refer to the [IIAB Architecture](https://github.com/iiab/iiab/wiki/IIAB-Architecture) and [IIAB Variables]( https://github.com/iiab/iiab/wiki/IIAB-Variables) pages for more information.

Installation
============

Before you start the installation please refer to the [hardware section of FAQ](http://wiki.laptop.org/go/IIAB/FAQ#What_hardware_should_I_use.3F) page for memory, storage and network requirements for your platform. Also note that downloading content might take a long time on slower Internet connections.

If you are a developer, please consider [building Internet-in-a-Box from scratch](https://github.com/iiab/iiab/wiki/IIAB-Installation#do-everything-from-scratch).

Please refer to the [IIAB Installation](https://github.com/iiab/iiab/wiki/IIAB-Installation) page for more information.

Setting up a development environment
=====================================
( This section uses an experimental development environment for Internet-in-a-Box. It is being developed in the [iiab-dev-mode repository](https://github.com/arky/iiab-dev-mode). )

This section provide a quick setup of Internet-in-a-Box (IIAB) development environment using [Vagrant](https://www.vagrantup.com/). You will need a computer with [virtualization enabled](https://www.virtualbox.org/manual/UserManual.html) and git, Vagrant (2.0 or later) and [VirtualBox](https://www.virtualbox.org/) installed.

## Requirements

 * git
 * [Vagrant (2.0 or later)](https://www.vagrantup.com/)
 * [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
 * Editor ([Atom](www.atom.io), Emacs, vi, etc)

## Setup Instructions
1. Check out the repository and its submodules onto your development machine.
`git clone --recursive git@github.com:arky/iiab-dev-mode.git`

2. Change directory into 'iiab-dev-mode' with `cd iiab-dev-mode`. You can update all the submodules to latest master using `git submodule foreach git pull origin master`

3. Set up a vagrant machine with `vagrant up` and provision it with `vagrant provision`. Please select the available bridge network interface (wlan0 or eth0) that connects your host machine to the Internet.

4. Connect to your vagrant machine with `vagrant ssh`. All your local development files available as shared folder in `/opt/iiab` directory.

5. Install IIAB itself from the Ansible playbooks by following [IIAB Installation](https://github.com/iiab/iiab/wiki/IIAB-Installation#do-everything-from-scratch) instructions:
```
   cd /opt/iiab/iiab/scripts/
   ./ansible

   cd /opt/iiab/iiab/
   ./iiab-install

   cd /opt/iiab/iiab-admin-console/
   ./install

   cd /opt/iiab/iiab-menu/
   ./cp-menus
```
6. Hack away!

7. You can commit your local changes to your personal forks of Internet-in-a-Box repository and then send pull request to IIAB project. Once you forked a repository, you change directory into that repository and setting a default git remote push setting with the following command.

   `cd <repo> && git remote set-url --push origin git@github.com:<your_username>/<your_forked_iiab_repo_name>.git`

	Learn more by reading blog post [Different git Push & Pull(fetch) URLs](http://blog.yuriy.tymch.uk/2012/05/different-git-push-pullfetch-urls.html) and the [Git Basics - Working with Remotes](https://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes) chapter of Scott Chacon and Ben Straub's "Git Pro" book.

8. Once you are done, you can stop your vagrant machine with `vagrant halt` or remove it completely with `vagrant destroy`.

Debugging
=========

Here are few strategies for debugging problems during the Internet-in-a-Box installation.

* When a installation task fails, Ansible halts printing out a descriptive error message to the screen. This error information is also written to `iiab-install.log` file within `/opt/iiab/iiab`. (Look through logs to check if any preceding line contains the error).
* When an installation succeeds, the last lines printed on the screen will look like the following (failed=0):
```
   PLAY RECAP *********************************************************************
   127.0.0.1                  : ok=405  changed=125  unreachable=0    failed=0
```
* Search through the Ansible playbooks using `egrep -rn <string from the failing step> /opt/iiab/iiab/roles/*>` to find the failed task.
* You can add additional [debug print statements](http://docs.ansible.com/ansible/latest/debug_module.html) to Ansible playbooks for debugging the problem.
* Talk to us or report a bug using the information below.

 Please refer to [Ansible playbook documentation](http://docs.ansible.com/ansible/latest/playbooks.html) for more information.

Testing your code with Travis CI
=================================

To maintain the quality of the Internet-in-a-Box (IIAB) code we use [Travis Continuous Integration (CI)](https://travis-ci.org) build infrastructure. Travis CI does tests to
ensure the code syntax is correct and the code is formatted properly using `ansible` syntax checker, `ansible-lint` and `ansible-review` tools. The results of Travis CI Internet-in-a-Box (IIAB) could be seen [here](https://travis-ci.org/iiab/iiab).

Every pull request is automatically tested by Travis CI. The results of these tests are added to the pull request. This aids Internet-in-a-Box (IIAB) developers in reviewing the quality of the code in a pull request.

To test your forked repository of Internet-in-a-Box (IIAB) code. You have to enable automatic build tests in your [Travis-ci.org](https://travis-ci.org) profile page.

* Login to [Travis-ci.org](https://travis-ci.org) using your Github account.
* Go to your Travis CI profile page and enable the repository you want to build.
* The builds will start whenever a new commit is pushed to your repository.

Please refer to [Travis CI documentation](https://docs.travis-ci.com/user/getting-started/) for more information.

Reporting Bugs
==============

You can file bug reports on [GitHub](https://github.com/):

* Sign up for a [GitHub](https://github.com/) account
* Go to the [issue tracker on GitHub](https://github.com/iiab/iiab/issues)
* Search for existing issues using the search field
* If you don't find any similar issues, file a new issue!

Please consider providing a descriptive title, your operating system information, error messages and steps to reproduce the issue.

Get in touch
============

* Join our [technology](http://lists.laptop.org/listinfo/server-devel) and [learning design](https://groups.google.com/group/unleashkids) mailing lists
* Join our [live calls](http://minutes.iiab.io) most Mondays and Thursday
* Join us on IRC live chat: [#schoolserver](https://webchat.freenode.net/?channels=#schoolserver) on [freenode]( https://www.freenode.net/)
* Post an idea or question to our [community forums](http://iiab.io/)
* Read our Frequently Asked Questions ([FAQ.IIAB.IO](http://FAQ.IIAB.IO))