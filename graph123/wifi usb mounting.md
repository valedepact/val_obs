check if usb is detected
--
lsusb
ip link show

└─$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 008: ID 1038:1122 SteelSeries ApS SteelSeries KLC
Bus 003 Device 010: ID 1038:1134 SteelSeries ApS SteelSeries ALC
Bus 003 Device 012: ID 5986:1160 Bison Electronics Inc. Integrated Camera
Bus 003 Device 015: ID 8087:0032 Intel Corp. AX210 Bluetooth
Bus 003 Device 026: ID 214b:7250 Huasheng Electronics USB2.0 HUB
Bus 003 Device 027: ID 0fe6:9900 ICS Advent 10/100M LAN
Bus 003 Device 028: ID 214b:7250 Huasheng Electronics USB2.0 HUB
Bus 003 Device 031: ID 1908:0226 GEMBIRD MicroSD Card Reader/Writer
Bus 003 Device 034: ID 0bda:f179 Realtek Semiconductor Corp. RTL8188FTV 802.11b/g/n 1T1R 2.4G WLAN Adapter
Bus 003 Device 053: ID 30fa:0400  USB OPTICAL MOUSE 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

----------
└─$ ip link show

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
    link/ether d8:bb:c1:21:a8:98 brd ff:ff:ff:ff:ff:ff
4: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN mode DORMANT group default qlen 1000                                      
    link/ether 32:c3:37:5b:d6:c0 brd ff:ff:ff:ff:ff:ff permaddr 14:18:c3:3a:2c:1c                                                                         
6: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN mode DEFAULT group default                                              
    link/ether ce:fc:f5:fc:d8:00 brd ff:ff:ff:ff:ff:ff
7: eth1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN mode DEFAULT group default qlen 1000                                      
    link/ether 68:e4:3b:30:a6:b9 brd ff:ff:ff:ff:ff:ff
11: wlan1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN mode DORMANT group default qlen 1000                                     
    link/ether 66:76:66:32:db:fe brd ff:ff:ff:ff:ff:ff permaddr 90:de:80:11:ed:de  

--------


check if driver is loaded
--
dkms status
iwconfig

└─$ dkms status
virtualbox/7.2.8, 6.19.14+kali-amd64, x86_64: installed

-------
└─$ iwconfig
Command 'iwconfig' not found, but can be installed with:
sudo apt install wireless-tools
Do you want to install it? (N/y)y
sudo apt install wireless-tools
[sudo] password for kali: 
The following packages were automatically installed and are no longer required:
  enchant-2                 libmbedcrypto16  libsox-fmt-base
  libabsl20240722           libmbedtls21     libsvtav1enc2
  libavc1394-0              libmbedx509-7    libteamdctl0
  libbabeltrace1            libnsl2          libunibreak6
  libboost-iostreams1.83.0  libpoppler147    libwoff1
  libboost-thread1.83.0     libpostal-data   libxmlsec1-1
  libgdal38                 libpostal1       libxmlsec1-openssl1
  libicu76                  libraw23t64      libzxing3
  libio-pty-perl            libsdl2-classic  postgresql-common-dev
  libipc-run-perl           libsimdutf31     python3-typeshed
  libllhttp9.3              libsodium23      python3-tz
Use 'sudo apt autoremove' to remove them.

Installing:
  wireless-tools
                                                                             
Installing dependencies:
  libiw30t64
                                                                             
Summary:
  Upgrading: 0, Installing: 2, Removing: 0, Not Upgrading: 31
  Download size: 100.0 kB
  Space needed: 284 kB / 105 GB available

Continue? [Y/n] y
Get:1 https://http.kali.org/kali kali-rolling/main amd64 libiw30t64 amd64 30~pre9-21 [17.2 kB]
Get:2 https://http.kali.org/kali kali-rolling/main amd64 wireless-tools amd64 30~pre9-21 [82.7 kB]
Fetched 100.0 kB in 3s (36.0 kB/s)        
Selecting previously unselected package libiw30t64:amd64.
(Reading database… 487145 files and directories currently installed.)
Preparing to unpack …/libiw30t64_30~pre9-21_amd64.deb…
Unpacking libiw30t64:amd64 (30~pre9-21)…
Selecting previously unselected package wireless-tools.
Preparing to unpack …/wireless-tools_30~pre9-21_amd64.deb…
Unpacking wireless-tools (30~pre9-21)…
Setting up libiw30t64:amd64 (30~pre9-21)…
Setting up wireless-tools (30~pre9-21)…
Processing triggers for kali-menu (2026.2.6)…
Processing triggers for libc-bin (2.42-16)…
Processing triggers for man-db (2.13.1-1)…
Scanning processes...                                                        
Scanning processor microcode...                                              
Scanning linux images...                                                     

Running kernel seems to be up-to-date.

The processor microcode seems to be up-to-date.

No services need to be restarted.

No containers need to be restarted.

No user sessions are running outdated binaries.

No VM guests are running outdated hypervisor (qemu) binaries on this host.


-------
Install drivers
--
sudo apt update
sudo apt install linux-headers-$(uname -r) build-essential

└─$ sudo apt install linux-headers-$(uname -r) build-essential

linux-headers-6.19.14+kali-amd64 is already the newest version (6.19.14-1+kali1).
linux-headers-6.19.14+kali-amd64 set to manually installed.
build-essential is already the newest version (12.12).
The following packages were automatically installed and are no longer required:
  enchant-2                 libmbedcrypto16  libsox-fmt-base
  libabsl20240722           libmbedtls21     libsvtav1enc2
  libavc1394-0              libmbedx509-7    libteamdctl0
  libbabeltrace1            libnsl2          libunibreak6
  libboost-iostreams1.83.0  libpoppler147    libwoff1
  libboost-thread1.83.0     libpostal-data   libxmlsec1-1
  libgdal38                 libpostal1       libxmlsec1-openssl1
  libicu76                  libraw23t64      libzxing3
  libio-pty-perl            libsdl2-classic  postgresql-common-dev
  libipc-run-perl           libsimdutf31     python3-typeshed
  libllhttp9.3              libsodium23      python3-tz
Use 'sudo apt autoremove' to remove them.

Summary:
  Upgrading: 0, Installing: 0, Removing: 0, Not Upgrading: 31


------
### Install the Driver (RTL8188FTV)

This chip needs an out-of-tree driver. The most maintained one is:
sudo apt update
sudo apt install git dkms linux-headers-$(uname -r) build-essential
git clone https://github.com/kelebek333/rtl8188fu
sudo dkms add ./rtl8188fu
sudo dkms build rtl8188fu/1.0
sudo dkms install rtl8188fu/1.0
sudo modprobe 8188fu

----

┌──(kali㉿kali)-[~]
└─$ sudo apt install linux-headers-$(uname -r) build-essential

linux-headers-6.19.14+kali-amd64 is already the newest version (6.19.14-1+kali1).
linux-headers-6.19.14+kali-amd64 set to manually installed.
build-essential is already the newest version (12.12).
The following packages were automatically installed and are no longer required:
  enchant-2                 libmbedcrypto16  libsox-fmt-base
  libabsl20240722           libmbedtls21     libsvtav1enc2
  libavc1394-0              libmbedx509-7    libteamdctl0
  libbabeltrace1            libnsl2          libunibreak6
  libboost-iostreams1.83.0  libpoppler147    libwoff1
  libboost-thread1.83.0     libpostal-data   libxmlsec1-1
  libgdal38                 libpostal1       libxmlsec1-openssl1
  libicu76                  libraw23t64      libzxing3
  libio-pty-perl            libsdl2-classic  postgresql-common-dev
  libipc-run-perl           libsimdutf31     python3-typeshed
  libllhttp9.3              libsodium23      python3-tz
Use 'sudo apt autoremove' to remove them.

Summary:
  Upgrading: 0, Installing: 0, Removing: 0, Not Upgrading: 31
┌──(kali㉿kali)-[~]
└─$ sudo apt install git dkms linux-headers-$(uname -r) build-essential
git is already the newest version (1:2.53.0-1).
dkms is already the newest version (3.2.2-1).
linux-headers-6.19.14+kali-amd64 is already the newest version (6.19.14-1+kali1).
build-essential is already the newest version (12.12).
The following packages were automatically installed and are no longer required:
  enchant-2                 libmbedcrypto16  libsox-fmt-base
  libabsl20240722           libmbedtls21     libsvtav1enc2
  libavc1394-0              libmbedx509-7    libteamdctl0
  libbabeltrace1            libnsl2          libunibreak6
  libboost-iostreams1.83.0  libpoppler147    libwoff1
  libboost-thread1.83.0     libpostal-data   libxmlsec1-1
  libgdal38                 libpostal1       libxmlsec1-openssl1
  libicu76                  libraw23t64      libzxing3
  libio-pty-perl            libsdl2-classic  postgresql-common-dev
  libipc-run-perl           libsimdutf31     python3-typeshed
  libllhttp9.3              libsodium23      python3-tz
Use 'sudo apt autoremove' to remove them.

Summary:
  Upgrading: 0, Installing: 0, Removing: 0, Not Upgrading: 31
┌──(kali㉿kali)-[~]
└─$ git clone https://github.com/kelebek333/rtl8188fu

Cloning into 'rtl8188fu'...
remote: Enumerating objects: 997, done.
remote: Counting objects: 100% (119/119), done.
remote: Compressing objects: 100% (57/57), done.
remote: Total 997 (delta 91), reused 67 (delta 62), pack-reused 878 (from 3)
Receiving objects: 100% (997/997), 9.15 MiB | 5.30 MiB/s, done.
Resolving deltas: 100% (509/509), done.             
┌──(kali㉿kali)-[~]
└─$ sudo dkms add ./rtl8188fu

Creating symlink /var/lib/dkms/rtl8188fu/1.0/source -> /usr/src/rtl8188fu-1.0
┌──(kali㉿kali)-[~]
└─$ sudo dkms build rtl8188fu/1.0 

Sign command: /lib/modules/6.19.14+kali-amd64/build/scripts/sign-file
Signing key: /var/lib/dkms/mok.key
Public certificate (MOK): /var/lib/dkms/mok.pub

Building module(s)...................... done.
Signing module /var/lib/dkms/rtl8188fu/1.0/build/rtl8188fu.ko
┌──(kali㉿kali)-[~]
└─$ sudo dkms install rtl8188fu/1.0

Installing /lib/modules/6.19.14+kali-amd64/updates/dkms/rtl8188fu.ko.xz
Running depmod.... done.
┌──(kali㉿kali)-[~]
└─$ sudo modprobe 8188fu

modprobe: FATAL: Module 8188fu not found in directory /lib/modules/6.19.14+kali-amd64

┌──(kali㉿kali)-[~]
└─$ 

-----
still on driver
--
┌──(kali㉿kali)-[~]
└─$ sudo modprobe rtl8188fu
┌──(kali㉿kali)-[~]
└─$ lsmod | grep 8188

rtl8188fu            1482752  0
cfg80211             1511424  5 iwlmvm,iwlwifi,mac80211,rtl8xxxu,rtl8188fu
usbcore               430080  12 xhci_hcd,usbnet,usbhid,btmtk,usb_storage,uvcvideo,btusb,xhci_pci,cdc_ether,rtl8xxxu,uas,rtl8188fu
┌──(kali㉿kali)-[~]
└─$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
docker0   no wireless extensions.

eth1      no wireless extensions.

wlan1     IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off             
┌──(kali㉿kali)-[~]
└─$ ip link show

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
    link/ether d8:bb:c1:21:a8:98 brd ff:ff:ff:ff:ff:ff
4: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN mode DORMANT group default qlen 1000                                      
    link/ether ce:04:46:75:01:d0 brd ff:ff:ff:ff:ff:ff permaddr 14:18:c3:3a:2c:1c                                                                         
6: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN mode DEFAULT group default                                              
    link/ether ce:fc:f5:fc:d8:00 brd ff:ff:ff:ff:ff:ff
7: eth1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN mode DEFAULT group default qlen 1000                                      
    link/ether 68:e4:3b:30:a6:b9 brd ff:ff:ff:ff:ff:ff
11: wlan1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN mode DORMANT group default qlen 1000                                     
    link/ether 06:be:6f:18:f8:bc brd ff:ff:ff:ff:ff:ff permaddr 90:de:80:11:ed:de                                                                        
┌──(kali㉿kali)-[~]
└─$ 

#Everything #is #working #perfectly. #wlan1 #is #your #RTL8188FTV #adapter. #next #is #connecting #to #a #network
## if you get a signingin or boot error
```bash
dmesg | tail -20
```
If it says "Required key not available", Secure Boot is blocking unsigned modules. Fix with:
```bash
sudo mokutil --disable-validation
```
then reboot

