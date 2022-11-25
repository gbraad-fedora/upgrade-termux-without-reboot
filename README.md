Fedora system upgrade without reboot
===================================

These instructions will allow you to perform a system upgrade without the need (or possibility) to 'reboot'. For example,
a reboot is not possible on Termux or WSL2. With these instructions you will trigger the update yourself.


On Termux start the environment as usual:
```
$ chmod 700 fedora-fs
$ ./start-fedora.sh
```
Note that during the update you need to change teh permission on a folder. Elsethe `upgrade` step will fail.

Make sure your system is fully up to date by running `dnf update -y` and has the `system-upgrade` command installed:

```
$ dnf install 'dnf-command(system-upgrade)'
```


### The actual process

```
$ dnf upgrade --refresh
$ dnf system-upgrade download --releasever=32
$ dnf system-upgrade reboot
$ dnf system-upgrade upgrade
```


#### Links

  * https://docs.fedoraproject.org/en-US/quick-docs/dnf-system-upgrade/


#### Notes

##### WSL2

This does not work when `systemd=true` has been set in `/etc/wsl.conf`. It somehow incorrectly shuts down with `reboot` and causes issues with connectivity on the `upgrade` step. For the moment, just disabled it and after the `reboot`/`upgrade` step you can re-enable it.