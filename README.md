PXE Boot
========

This project is basically so I can take notes and make it a repeatable process.

#### The problem:

I don't have a DVD-R and my Asus UL50vt doesn't feel like booting from USB.  So that leaves PXE.

## Resources:

#### DHCP/TFTP on OSX

- [OSX DHCP Server](http://www.jacquesf.com/2011/04/mac-os-x-dhcp-server/)
- [OSX Instructions](http://ruby-journal.com/install-ubuntu-with-pxe-via-osx/)
- [OSX TFTP Server](http://ww2.unime.it/flr/tftpserver/)

#### PXE with Arch

- [Arch PXE Instructions](https://wiki.archlinux.org/index.php/PXE)
- [Arch PXE Images](https://releng.archlinux.org/pxeboot/#undi_pxeimage)

## Process

#### Setup TFTP Server

1. Download the [Arch PXE Images](https://releng.archlinux.org/pxeboot/#undi_pxeimage)
  - Look under "Using an iPXE image"
  - Create a TFTP root folder and move the image here.
  - For demonstration purposes only `$TFTPROOT=your/tftp/root`
  - Chown the TFTP root folder with `sudo chown -R nobody:nogroup $TFTPROOT`
1. Download, install, and open [OSX TFTP Server](http://ww2.unime.it/flr/tftpserver/)
1. In the application, change TFTP root to the desired folder.
1. After setting the folder - Click both fix permissions buttons.
1. Click "Start Server"

#### Setup DHCP Server

1. Install isc-dhcp with `brew install isc-dhcp`
1. Copy example conf with `cp [git repo root]/dchpd.conf.example /usr/local/etc/dhcpd.conf`
1. Pupulate the Mac Address *??:??:??:??:??:??*
1. Start the server with

After you're done, uninstall the DHCP server with `brew uninstall isc-dhcp`

#### Setup Eth0 Interface
