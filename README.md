= tips and tricks for wsl
:numbers:
:toc:

Windows Subsystem for Linux (Wsl) is a feature that allows you to run linux in a virtual machine.
You can manage the machine from PowerShell with the command "wsl".

== helpfull commands in windows power shell

update wsl
[source,bash]
----
wsl --update
----

list machines
[source,bash]
----
wsl --list

----

shutdown machine
[source,bash]
----
wsl --shutdown
----

show status
[source,bash]
----
wsl --status
----

== helpfull commands / configs in ubuntu

=== update sw packages
[source,bash]
----
apt update 
apt full-upgrade 
----

=== enable systemd
Create file /etc/wsl.conf and place following lines intoo that file.

[source,bash]
----
[boot]
systemd=true
----

==== install smartgit

[source,bash]
----
sudo apt install libgtk-3-0 git 
mkdir ~/tools
cd tools
wget https://www.syntevo.com/downloads/smartgit/smartgit-linux-23_1_1.tar.gz
tar xzf smartgit-linux-23_1_1.tar.gz
rm smartgit-linux-23_1_1.tar.gz
~/tools/smartgit/bin/smartgit.sh
----

=== USB

==== Installation in windows
the following article shows how to allow wsl machine access to usb device
- https://learn.microsoft.com/en-us/windows/wsl/connect-usb

==== Install the USBIP tools and hardware database in Linux
[source,bash]
----
sudo apt install linux-tools-generic hwdata
sudo update-alternatives --install /usr/local/bin/usbip usbip /usr/lib/linux-tools/*-generic/usbip 20
----

==== manage usb devices in windows powershell

attach usb devices
[source,bash]
----
usbipd list
usbipd bind --busid 2-13
usbipd attach --busid 2-13 -w Ubuntu
----

detach usb devices
[source,bash]
----
usbipd list
usbipd bind --busid 2-13
usbipd detach  --busid 2-13 -w Ubuntu
----

NOTE: you can check if usb device is available inside wsl2 machine by command "lsusb".

== Bookmarks
* wsl installation procedure wsl installation procedure https://learn.microsoft.com/en-us/windows/wsl/install
* https://learn.microsoft.com/en-us/windows/wsl/connect-usb

