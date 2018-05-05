# OSR Debian Installer

Tools for building Debian/Ubuntu hands-off automated install
images. Basic operation goes as follows:
* Unpack a downloaded standard net-install image to a work area.
* In the work area, uncompress the contents of the initrd image.
* Use the m4 macro processor to create file "preseed.cfg" from a template, setting custom variables as needed. Add preseed.cfg to the work area root.
* Use m4 to patch script "finalize" to set the default username. Add finalize to the work area root. This script runs upon completion of initialization, to perform any further configuration or cleanup.
* Add script "find_disk" to the work area root. This script tries to determine the disk upon which the operating system and bootloader should be installed, and runs just before the disk partitioning stage.
* Embed preseed.cfg, finalize and find_disk in initrd, recompress.
* Delete preseed.cfg, finalize, find_disk from work area.
* Remaster ISO image.
