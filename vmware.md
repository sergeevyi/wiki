# VMWare Tool installation 

Run this command to extract the contents of the VMware Tools bundle:

tar xzvf /mnt/cdrom/VMwareTools-x.x.x-xxxx.tar.gz -C /tmp/

Note: x.x.x-xxxx is the version discovered in the previous step.

Run this command to change directories into the VMware Tools distribution:

cd /tmp/vmware-tools-distrib/

Run this command to install VMware Tools:

sudo ./vmware-install.pl
