# Introduction
The escore-build project builds everything in a clean mock chroot environment just like redhat/centos does.

The iso build process is based on lorax - a open source iso build tool from redhat/centos. The result iso is anaconda install iso - yet another redhat/centos open source software.

# Scripts
* setup.sh:

  Copy the necessary settings and initialize mock environment. This script should be used before running other scripts. Some options are also available on demand:
  
  | Option | Description |
  | ------ | ----------- |
  | --server= | modify the default server address. |
  | --config= | change the configuration set. |

* build_iso.sh:

  Build "EasyStack Cloud Linux" ISO image.

* make_repos.sh:

  Create easystack repository for mock / installer / iso environment. After running this script, one must copy the result to the server with httpd service.

* shell.sh:

  Enter mock environment if one would like to try some commands.

* clean.sh:

  Cleanup mock cache and all the stuff we created.

# Notes
1. Since we use mock environment to build packages and iso image, a user should become a member of the mock group by adding their username to the mock line in /etc/group. This can be done with the following command:

```
$ sudo /usr/sbin/usermod -a -G mock $USER
```
  
2. During the process we need stuff provided by http service from remote. So make sure that the services are available on the server and the directory locations are correct.

```
http://[server]/ESCL/7.3.1611/os
http://[server]/ESCL/7.3.1611/updates
``