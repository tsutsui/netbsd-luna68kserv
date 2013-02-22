luna68kserv - NFS Server Kit for NetBSD/luna68k client


1. What's luna68kserv

This "luna68kserv" image provides easy setup for OMRON LUNA-I workstation
to boot NetBSD/luna68k without installation to internal SCSI drives using
"root file system on NFS" environment.


2. What luna68kserv image contains

This image contains a bootable NetBSD/i386 file system image that
automatically starts daemons like isibootd(8), dhcpd(8), mountd(8),
and nfsd(8), and it also contains an NFS exported NetBSD/luna68k
file system which has all release binaries including X server and clients.


3. Requirements

- x86 based PC with NIC which can boot from USB devices
- 10BASE-T cross cable (or HUB)
- the original LUNA (note LUNA-II doesn't support netboot)


4. How to use luna68kserv

1) write image to 2GB (or larger) USB flash memory via gzip(1) and dd(1)
   (or Rawrite32.exe tool for Windows),
    Rawrite32.exe tool can be found here:
    http://www.NetBSD.org/~martin/rawrite32/
2) put it on your x86 PC and boot it (per machine specific procedure)
3) edit /etc/ethers and put MAC address of your LUNA
   note to check LUNA's MAC address see NetBSD/luna68k info page:
   http://www.NetBSD.org/ports/luna68k/info.html#determine_ether_address
4) connect LUNA to the x86 luna68kserv PC via 10BASE-T cross cable etc.
   note: luna68kserv runs dhcpd(8) with its own address (10.0.0.xxx)
   so don't connect it to your open network.
5) boot LUNA via Ethernet from the monitor prompt:
---
>k
ctlr: dk  et
host: omron
sver: servername
fnam: omron:vmunix  luna68kserv:boot
>g
text(71800)+data(0)+bss(21912) 
>x
 
>> NetBSD/luna68k boot, Revision 1.4 (Fri Feb 22 20:43:41 JST 2013)
>> (based on Stinger ver 0.0 [Phase-31])

 :
---
   more examples are here:
   https://gist.github.com/tsutsui/4546851
6) have fun!
   see afterboot(8) man page for more setup
   http://netbsd.gw.com/cgi-bin/man-cgi?afterboot++NetBSD-6.0
   http://ftp.netbsd.org/pub/NetBSD/misc/enami/afterboot.txt

---
Izumi Tsutsui
