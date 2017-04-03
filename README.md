# avahiswitch

Raspberry Pi service to turn on avahi-daemon if /boot/avahi is present.  

To be used with ethernet gadget mode to allow to image Sticky Fingers Kali-Pi and enable
ethernet gadget mode by editing the following two files in the /boot partition:
**_cmdline.txt_**: Add “modules-load=dwc2,g_ether” after “rootwait”  
**_config.txt_**: Add “dtoverlay=dwc2“  

#### To use the Service:
Add a file called "**_avahi_**" in /boot will enable the avahi-daemon, which in turn makes the raspberry pi discoverable via the name "**kali-pi.local**".

This is particularly useful when using ethernet gadget mode for the initial headless setup of a raspberry pi.  
I advise to disable the avahi-daemon service after the initial setup (systemctl disable avahi-daemon).  

#### To install the service:  

*sudo cp avahiswitch.service /lib/systemd/system/*  
*sudo cp -f avahi-daemon.conf /etc/avahi/*  
*systemctl enable avahiswitch.service*  
