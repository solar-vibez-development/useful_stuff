# Fn keys Brightness Control (several ASUS laptops)

In the terminal:

```shell
sudo gedit /etc/default/grub
```
Change
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="

```
Save, then
```shell
sudo update-grub
```
#Re-enable Jayatana (Ubuntu 15.04/15.10)

If this doesn't affect the applications you're using, you can re-enable **JAyatana** globally, by creating a file called `jayatana.conf` under `/usr/share/upstart/sessions/` and paste this in the file:
```
description "Java Ayatana"

start on starting dbus

script
 initctl set-env --global JAVA_TOOL_OPTIONS="-javaagent:/usr/share/java/jayatanaag.jar $JAVA_TOOL_OPTIONS"
end script
```
Then save the file, restart the session and Unity's global menu and HUD should work again for Java Swing applications.

You can also enable it on a per-program basis, by adding the following line in the program start script, etc.:
```
JAVA_TOOL_OPTIONS="-javaagent:/usr/share/java/jayatanaag.jar $JAVA_TOOL_OPTIONS"
```
