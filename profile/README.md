# AntiUbuntuPython
*No, general OS shouldn't depend on Python. Even if Ubuntu.*

## What?
The several packages depend on Python 3.8 and declare `Breaks` for Python 3.9 or later. This is very annoying.
So, we're here for alter those package to be not depending (effectively).

## How remove Python?
### Remove packages depending on `python3` package
Example:
* [`focal:obs-studio`](https://packages.ubuntu.com/focal/obs-studio) - It seems that the Python installation is optional, but package is requiring python. [Bionic](https://packages.ubuntu.com/bionic/obs-studio) doesn't have this issue.
* [`focal:obs-plugins`](https://packages.ubuntu.com/focal/obs-plugins) - Same as `obs-studio`. Bionic doesn't have this issue.
* [`ansible`](https://packages.ubuntu.com/focal/ansible) - written in Python ([wikidata](https://www.wikidata.org/wiki/Q2852503)). You must avoid it.
* [`ubuntu-minimal`](https://packages.ubuntu.com/focal/ubuntu-minimal) - It looks like necessary package, but it's not. It's just a meta-package.
* [`apturl`](https://packages.ubuntu.com/focal/apt-url) - use https://github.com/AntiUbuntuPython/apt-url-glue instead.
* [`apport`](https://packages.ubuntu.com/focal/apport) - It is kernel-level crush-handler. Can removed safely.
* [`unattended-upgrades`](https://packages.ubuntu.com/focal/unattended-upgrades) - It is periodic `apt upgrade` handler. Can removed safely (if your machines are not sensitive).
* [`mate-menu`](https://packages.ubuntu.com/focal/mate-menu) / [`mate-tweak`](https://packages.ubuntu.com/focal/mate-tweak) / [`mate-dock-applet`](https://packages.ubuntu.com/focal/mate-dock-applet) - no solutions―yet.
* [`lsb-release`](https://packages.ubuntu.com/focal/lsb-release) - use https://github.com/AntiUbuntuPython/lsb-release-rs instead.
* [`netplan.io`](https://packages.ubuntu.com/focal/netplan.io) - [`ipupdown`](https://packages.ubuntu.com/focal/ifupdown) [can be used](https://askubuntu.com/a/1402387/1187317)
* [`cloud-init`](https://packages.ubuntu.com/focal/cloud-init) - This package depends both `netplan.io` and `python3`. You must avoid this.
* [`ubuntu-drivers-common`](https://packages.ubuntu.com/focal/cloud-init) - This package depends python3-apt, python3-xkit, python3-click.
  * NOTE: Perhaps you should not remove this package. This is depended from `nvidia-common`, `ubuntu-desktop`, `mate-desktop`, and so on.
* [`software-properties-common`](https://packages.ubuntu.com/focal/cloud-init) - This provides `add-apt-repository(1)`, but [same effect can be archived by editing sourcefile manually](https://unix.stackexchange.com/a/22696/471115).

### After removing
Now you can `sudo apt remove python3`! Then reboot. If all thihgs are working fine, then cograts. You've well done!
