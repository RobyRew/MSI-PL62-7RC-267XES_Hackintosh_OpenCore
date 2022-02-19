# Hackintosh Guide for **MSI PL62 7RC-267XES** and maybe similar **7RC** models

**This guide it's updated to OpenCore 0.7.8.**
<!-- shields -->
<div>
    <!-- downloads -->
    <a href="https://github.com/RobyRew/MSI-PL62-7RC-267XES_Hackintosh_OpenCore/releases">
        <img src="https://img.shields.io/github/downloads/RobyRew/MSI-PL62-7RC-267XES_Hackintosh_OpenCore/total" alt="downloads"/>
    </a>
    <!-- version -->
    <a href="https://github.com/RobyRew/MSI-PL62-7RC-267XES_Hackintosh_OpenCore/releases/latest">
        <img src="https://img.shields.io/github/release/RobyRew/MSI-PL62-7RC-267XES_Hackintosh_OpenCore.svg" alt="latest version"/>
    </a>
    <!-- platform -->
    <a href="https://github.com/RobyRew/MSI-PL62-7RC-267XES_Hackintosh_OpenCore">
        <img src="https://img.shields.io/badge/platform-macOS-lightgrey.svg" alt="platform"/>
    </a>
</div>
</br></br>

![Asus FX504GE running macOS Big Sur](#/Docs/Images/MSI-PL62-7RC-267XES-macOS.png)

[Amazon Page](https://www.amazon.es/MSI-PL62-7RC-267XES-Ordenador-i5-7300HQ/dp/B078ZZ4PJ1)


## Specs:
| Component | Name |
|:--- |:---:|
| Motherboard:  | MS-16JD1 **HM170** |
| CPU: | Intel i5-7300HQ |
| RAM: | 16GB **SK Hyinix** HMA82GS6CJR8N-VK 2666Mhz |
| iGPU: | Intel HD 630 (Mobile) |
| dGPU: | NVIDIA GeForce MX150 (DISABLED) |
| NVMe: | Silicon Motion SM2263XT |
| HDD: | HGST HTS541010B7E610 |
| Wifi/BT: | Intel Wireless-AC 3168NGW [Stone Peak] |
| Audio: | Realteck ALC892 |
| Ethernet: | Atheros QCA8171 |
| Trackpad: | SynPS/2 Synaptics TouchPad |
| Keyboard: | AT Translated Set 2 keyboard |

![MSI PL62 7RC-267XES Layout](#/Docs/Images/Guide/MSI-PL62-7RC-267XES-layout.png)
These are all the external ports of the laptop. (**They work**)

### Working
- [x] **Tested with macOS Catalina, Big Sur, and Monterrey**
- [x] **Wifi** (Thanks to [AirportItlwm.kext](https://github.com/OpenIntelWireless/itlwm/releases) and loading from system the kext: `IO80211Family.kext`)
- [x] **Bluetooth:** (Thanks to [IntelBluetoothFirmware.kext](https://github.com/OpenIntelWireless/IntelBluetoothFirmware/releases))
- [x] **Audio:** Intel CM238 (Thanks to AppleALC.kext with layout-id=3 setted in Device Properties)
- [x] **USB:** All internal and external ports (Thanks to SSDT-EC-USBX-LAPTOP.aml)
- [x] **Ethernet:** Atheros QCA8171 (Thanks to AtherosE2200Ethernet.kext)
- [x] **Trackpad:** (Partially Working thanks to VoodooI2C.kext, VoodooI2CHID.kext and SSDT-XOSI.aml)
- [x] **HDMI:** Works almost perfect. 
- [x] **Shutdown:** Yes
- [x] **Restart:** Yes
- [x] **Sleep/Wake:** Yes

### Not working
- Sleep/Wake/Restart/Shutdown not all working.
- Trackpad PC/2 Synaptic click (physical button and tapping) doesn't work.
- dGPU (Any support).
- No battery management.
- Continuity Features (not working for now, waiting on https://openintelwireless.github.io/).


```bash
```

# INSTALLATION GUIDE

---

## Making the Booteable USB

### From macOS:
[**Link to Apple's Guide**](https://support.apple.com/en-us/HT201372)

**Download installers:** [Monterrey Beta 10](http://swcdn.apple.com/content/downloads/21/10/002-17762-A_GUNYNIZ0PW/witdqh4bei493fvgin01qavvy1dfhcb87w/InstallAssistant.pkg)(Execute de .pkg to extract the installer) - [Big Sur](https://itunes.apple.com/us/app/macos-big-sur/id1526878132) - [Catalina](https://itunes.apple.com/us/app/macos-catalina/id1466841314) - [Mojave](https://itunes.apple.com/us/app/macos-mojave/id1398502828) - [High Sierra](https://itunes.apple.com/us/app/macos-high-sierra/id1246284741)

1. Connect a >=16 GB pendrive.
2. Open *Disk Utility* and Erase the USB with the name: *MyVolume*.
3. Open *Terminal* and use the proper commands for your macOS installer:
- Monterrey: `sudo /Applications/Install\ macOS\ 12\ Beta.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume`
- Big Sur: `sudo /Applications/Install\ macOS\ Big\ Sur.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume`
- Catalina: `sudo /Applications/Install\ macOS\ Catalina.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume`
- Mojave: `sudo /Applications/Install\ macOS\ Mojave.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume`
- High Sierra: `sudo /Applications/Install\ macOS\ High\ Sierra.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume`

![Terminal](/Docs/Images/Guide/BootableUSB.png)

### From Windows:

[**Link to Dortania's Guide**](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/winblows-install.html)

### From Linux:

[**Link to Dortania's Guide**](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/linux-install.html)


---

# BIOS Settings:
- Make Sure you have [Latest BIOS v*E16JDIMS.10F*](https://es.msi.com/Content-Creation/support/PL62-7RC#down-bios)
- After Updating the BIOS, stock configuration works, so don't worry about this part.

---

# OpenCore Configuration

## [Here it's my config.plist and the explanation:](/Docs/config.plist.md)
#### [ACPI](/Docs/config.plist.md#acpi)
#### [Booter](/Docs/config.plist.md#booter)
#### [DeviceProperties](/Docs/config.plist.md#deviceproperties)
#### [Kernel](/Docs/config.plist.md#kernel)
#### [Misc](/Docs/config.plist.md#misc)
#### [NVRAM](/Docs/config.plist.md#nvram)
#### [PlatformInfo](/Docs/config.plist.md#platforminfo)
#### [UEFI](/Docs/config.plist.md#uefi)

---

# Post Install
Open Terminal.app and run those commands:
```bash
sudo rm /Library/Preferences/SystemConfiguration/NetworkInterfaces.plist
sudo rm /Library/Preferences/SystemConfiguration/preferences.plist
```
---

# BenchMarks:
#### Cinebench R23:
![Cinebench R23](/#Docs/Images/Benchmarks/Cinebench_R23.png)

#### GeekBench 5:
![GeekBench 5_CPU Score](#/Docs/Images/Benchmarks/GeekBench5_CPU.png)
![GeekBench 5_GPU Score](#/Docs/Images/Benchmarks/GeekBench5_GPU.png)
https://browser.geekbench.com/v5/cpu/5707123

---

# Credits

[Apple](https://apple.com) (macOS)

[OpenCore Team](https://github.com/acidanthera/OpenCorePkg) (Bootloader)

[Dortania](https://dortania.github.io/OpenCore-Install-Guide/config-laptop.plist/coffee-lake.html#starting-point) (Guide)

[juanlatorre](https://github.com/juanlatorre/MSI-PL62-7RC-OC-Hackintosh) (EFI Base)

---

If this guide has been useful for you, don't forget to give me a star ⭐️❤️
