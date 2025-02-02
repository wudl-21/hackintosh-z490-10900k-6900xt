# Overview
## Description
* An EFI build for hackintoshes, using OpenCore as boot manager

## Specification
### OpenCore
* version 1.0.0
### Hardware
| Component | Spec | Remarks |
| --- | --- | --- |
| Motherboard | ASUS Proart Z490-Creator 10G | BIOS version: 3001, On-board LAN adapter: Intel I225-V, Audio: Realtek AS1220A |
| CPU | Intel Core i9-10900K | iGPU: UHD Graphics 630 |
| dGPU | AMD Radeon RX 6900 XT Liquid Cooled | Navi 21, ~~XTX~~ XTXH, Device ID: ~~73BF~~ 73AF |
| RAM | Crucial DDR4 3200 16Gx4 | / |
| Disk drive | Samsung SSD 860 EVO 1TB | SATA drive |
| WLAN adapter | Apple/Broadcom BCM943602CDP AX_2 | WiFi & Bluetooth support, connect to motherboard via a MiniPCIE-to-PCIEx4 adapter |
### macOS
* macOS 12.7.5 Monterey

## Functionality
| Name | Status | Remarks |
| --- | :---: | --- |
| Display | ✔️ | verified: 4K resolution support |
| Audio | ✔️ | verified: on DP |
| Sleep & Power | ✔️ | verified: Sleep, Wake, Shutdown, Restart |
| Wireless | ✔️ | verified: WiFi, Bluetooth, AirDrop |
| OS Features | ✔️ | verified: App Store, iTunes Store. Need [SMBIOS](#smbios) |
| iGPU related | ✔️ | verified: VDA support |
| dGPU related | 🔶 | need [GPU Spoofing](#gpu-spoofing) |
| USB | 🔶 | need [USB Mapping](#usb-mapping) |
| Ethernet | 🔶 | need [LAN firmware patching](#lan-firmware-patching) |
| ThunderBolt | ❓ | lack devices |
* Legend: ✔️=working, 🔶=working but config needed, ❓=not verified

# Before you start
* To make the EFI working for your machine, you have to modify multiple entries in `config.plist` and ACPI files. Methods like ProperTree can do the job but are not that decent. It is highly recommended to use [these tools](#useful-tools).

# Get it working
> I have downloaded the EFI folder and copied it into my EFI partition, what else should I do to make my hackintosh working?
* The EFI provided by this repo works fine with my machine, but it is highly dependent on hardware configuration and subject to changes, so it is recommended that you should make some modification based on your own machine.

## Useful Tools
* [OpenCore Auxiliary Tools (OCAT)](https://github.com/ic005k/OCAuxiliaryTools) - easy `config.plist` management
* [Hackintool](https://github.com/benbaker76/Hackintool) - debug and system info viewer
* [MaciASL](https://github.com/acidanthera/MaciASL) - ACPI editing
## SMBIOS
* You may follow [this guide](https://chriswayg.gitbook.io/opencore-visual-beginners-guide/step-by-step/oc-auxiliary-tools#platform-info) Don't know which one to choose? See [this guide](https://dortania.github.io/OpenCore-Install-Guide/extras/smbios-support.html#how-to-decide).
## BIOS Setting
* You may follow [this guide](https://www.tonymacx86.com/threads/storks-thunderball-ii-build-asus-proart-z490-creator-thunderbolt-3-i5-10400-rx-580.305775/#BIOS).
## USB Mapping
* You may follow [this repo](https://github.com/USBToolBox/tool).
## GPU Spoofing
> 6900XT cards of the XTX varaint work fine under macOS >=11. However, the XTXH variant of the 6900XT are not natively supported currently.
* You may refer to [this repo](https://github.com/TylerLyczak/Unsupported-6900XT-Hackintosh-Fix).
## LAN firmware patching
> The stock firmware for the Intel I225-V used on some of Z490 boards contains an incorrect Subsystem-ID and Subsystem Vendor-ID that causes the LAN issues. If you are interested in the technical backgrounds, you may refer to [this repo](https://github.com/5T33Z0/Gigabyte-Z490-Vision-G-Hackintosh-OpenCore/blob/main/I225-V_FIX.md#preparations).
* The system should work fine without Ethernet connection, but if you do need it, the steps in [this guide](https://benjenq.pixnet.net/blog/post/47745510) are necessary or you may encounter system crashes.

# Credit
* The EFI build provided here is based on [this repo](https://github.com/TylerLyczak/Hackintosh-10850k-ASUS-Z490-XII-Hero-6900XT).
