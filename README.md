### Before install Displaylink

```bash
--------------- Linux system info ----------------

Distro: Debian
Release: bookworm
Kernel: 6.1.0-21-amd64

---------------- DisplayLink info ----------------

Driver version: 
DisplayLink service status: 
EVDI service version: /sys/devices/evdi/version not found

------------------ Graphics card -----------------

Vendor: i915
Subsystem: [UHD
VGA: Intel Corporation CoffeeLake-S GT2 [UHD Graphics 630]
VGA (3D): 
X11 version: 21.1.7-3+deb12u8

-------------- DisplayLink xorg.conf -------------

File: /etc/X11/xorg.conf.d/20-displaylink.conf
cat: /etc/X11/xorg.conf.d/20-displaylink.conf: No such file or directory
Contents:
 

-------------------- Monitors --------------------

Providers: number : 1
Provider 0: id: 0x46 cap: 0xf, Source Output, Sink Output, Source Offload, Sink Offload crtcs: 3 outputs: 5 associated providers: 0 name:modesetting
```

## Manual Install DisplayLink

```bash
mkdir displaylink_manual
cd displaylink_manual
git clone https://github.com/DisplayLink/evdi.git
# please MANUALLY download this file before executing:
./displaylink-driver-x.x.x-xx.xxx.run --target displaylink --noexec
cd displaylink
tar -czf evdi.tar.gz -C ../evdi .
sudo ./displaylink-installer.sh uninstall
sudo rmmod evdi
sudo ./displaylink-installer.sh noreboot
sudo systemctl start displaylink-driver.service
```

Note: Brigtness GNOME addons "Soft Brigtness Plus"

change the brightness via an alpha layer, because feature DDC is not available on displaylink  

Ref :

https://github.com/DisplayLink/evdi/issues/413

https://www.reddit.com/r/Fedora/comments/yxkm3w/fedora_37_anybody_know_how_to_get_displaylink_to/


#### After Install DisplayLink

```bash

--------------- Linux system info ----------------

Distro: Debian
Release: bookworm
Kernel: 6.1.0-30-amd64

---------------- DisplayLink info ----------------

Driver version: 1.14.8
DisplayLink service status: up and running
EVDI service version: 1.14.8

------------------ Graphics card -----------------

Vendor: i915
Subsystem: [UHD
VGA: Intel Corporation CoffeeLake-S GT2 [UHD Graphics 630]
VGA (3D): 
X11 version: 21.1.7-3+deb12u8

-------------- DisplayLink xorg.conf -------------

File: /etc/X11/xorg.conf.d/20-displaylink.conf
cat: /etc/X11/xorg.conf.d/20-displaylink.conf: No such file or directory
Contents:
 

-------------------- Monitors --------------------

Providers: number : 5
Provider 0: id: 0x46 cap: 0xf, Source Output, Sink Output, Source Offload, Sink Offload crtcs: 3 outputs: 5 associated providers: 4 name:modesetting
Provider 1: id: 0xfc cap: 0x2, Sink Output crtcs: 1 outputs: 1 associated providers: 1 name:modesetting
Provider 2: id: 0xdb cap: 0x2, Sink Output crtcs: 1 outputs: 1 associated providers: 1 name:modesetting
Provider 3: id: 0xba cap: 0x2, Sink Output crtcs: 1 outputs: 1 associated providers: 1 name:modesetting
Provider 4: id: 0x98 cap: 0x2, Sink Output crtcs: 1 outputs: 1 associated providers: 1 name:modesetting

-------------------------------------------------------------------
```
