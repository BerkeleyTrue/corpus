---
title: linux
---

## Multi monitor changes

On Delora, adding a second monitor required opening nvidia settings manager with
sudo privileges to changes the /etc/X11/xorg.conf settings.

This will affect lightdm and i3 settings.

### Polybar changes

The polybar startup script required changes to automate adding generic bars to
extra monitors with i3 window displays

## lightdm

lightdm is a desktop manager. It launches a greater (lightdm-webkit2-greeter)
which displays a login page. The dm manages making auth requests to linux PAM
and juggling the changes of session into X11.

### notables

* ligth dm logs are root wr only. You need root privileges to access/view/edit
* X11 logs during this startup are at /var/log/Xorg.<n>.log where n is the x
    session number (?)
* Errors during x startup are loged to ~/.xsession-errors

### login bug

An invalid symbol in bash script loaded at start up caused the lightdm to loop
the login screen with no feedback.

## See Also

[terminal-shortcuts]

[terminal-shortcuts]: <./corpusterminal-shortcuts.md>
