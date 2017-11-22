# RPB-HAT stands for Remote Power Button Hat board
## This is for a remote power control with GEEEKPI's new designed board.
## It's a nice power controller board for your project which needs power on/off/reboot by remote controller.
## It also supports press button onboard.
## And you can use it on your Raspberry Pi 3 module B, and with operating system: Raspbian.
### How to use it ###
* Just download it from https://github.com/geeekpi/RPB.git by:
* cd ~
* git clone https://github.com/geeekpi/RPB.git
* cd RPB/
* sudo cp -Rvf remoteswitch /etc/init.d/
* sudo chmod +x /etc/init.d/remoteswitch
* sudo cat > /etc/rc.local <<EOF
<pre>
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# Print the IP address
_IP=$(hostname -I) || true
if [ "$_IP" ]; then
  printf "My IP address is %s\n" "$_IP"
fi

sudo gpio mode 7 out
sudo gpio write 7 1

exit 0
</pre>
EOF
* sudo chmod +x /etc/rc.local
* Reboot your raspberry and try to press the power button, reboot button and test it.
## Have fun!
