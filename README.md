Fedora system update without reboot
===================================

These instructions will allow you to perform a system upgrade without the need (or possibility) to 'reboot'. For example,
a reboot is not possible on Ternux or WSL2. With these instructions you will trigger the update yourself.


On Termux start the environment as usual:
```
$ chmod 700 fedora-fs
$ ./start-fedora.sh
```
Note that during the update you need to change teh permission on a folder. Elsethe `upgrade` step will fail.

Make sure your system is fully up to date by running `dnf update -y`.


### The actual process

```
$ dnf upgrade --refresh
$ dnf system-upgrade download --releasever=32
$ dnf system-upgrade reboot
$ dnf system-upgrade upgrade
```