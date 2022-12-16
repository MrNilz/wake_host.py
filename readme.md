# Wake Host Daemon

If you have a local DNS-Server Running and an other server that goes to sleep; but hat wake on lan (WOL) enabled you can use this script to wake your sleeping server with a magic package every time the DNS of your sleeping server is queried. 


Credit for the procd and config goes to: https://openwrt.org/docs/guide-developer/procd-init-script-example

# Config
Change the values in etc/config/wake_host to the desired values

# Install

## Prequisites

You need Python, "scapy" and "wakeonlan" installed where you want to run the script (on your local DNS Server)

## Install on local DNS

Just copy the files to the corresponding destinations on your local DNS. 

To enable the service when the server restarts
 `/etc/init.d/wake_host enable` 

Note: You might need to flag /etc/init.d/wake_host executable before you can to this.
 `chmod +x /etc/init.d/wake_host`

To immediately start the service use
 `/etc/init.d/wake_host start`

You can look in your syslog for a corresponding message. Pls note depending on your HW resources python can take quite some time for startup.

# Hints

To enhance startup time you can precompile python to pyc files using.

`python -m compileall /var/wake_host.py`