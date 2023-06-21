# EFI for Intel Desktop 12600K - Opencore 0.9.3 - Z690M AORUS ELITE DDR4 - macOS Ventura 13.4.1 - AMD RX 5500XT

Note|Description
:----|:----
macOS|Ventura 13.4.1
Motherboard|Gigabyte Z690M AORUS ELITE DDR4
GPU|AMD RX 5500XT
Processor|Intel® Core™ i5-12600K
NVME SSD|XPG S41 TUF 512Gb
RAM|2x XPG Gammix D45 8Gb 3600Mhz DDR4
Wifi/Bluetooth | WIFI 6E FENVI FV-AXE3000RGB - AX210 - Bluetooth 5.2
Ethernet | Intel® I225-V 2.5GbE LAN
SMBIOS | iMacPro1,1

- Opencore version: 0.9.3

# Basic Steps

1. Generate and complete your SMBIOS infos - **ALWAYS**;
2. Adjust your BIOS;
3. Install macOS and enjoy :)
4. Rempap USB ports (if needed) - **ALWAYS**;

Update **config.plist** in PlatformInfo > Generic with YOUR informations.
<br><br>
*1. MLB (Board Serial)
<br>
2. ROM (Mac Address)
<br>
3. SystemSerialNumber (Serial)
<br>
4. SystemUUID (SmUUID)*

Please use [*genSMBIOS*](https://github.com/corpnewt/GenSMBIOS/archive/refs/heads/master.zip) for generate values for above itens.
<br>
Please use [*ProperTree*](https://github.com/corpnewt/ProperTree/archive/refs/heads/master.zip) for configure/edit your config.plist.

# Compatible SMBIOS

SMBIOS|Description
:----|:----
MacPro7,1|Because GPU integrated in 12th gen without support for Apple.
iMacPro1,1|Because GPU integrated in 12th gen without support for Apple.

# BIOS Settings

### Disable
- Fast Boot
- Secure Boot
- Serial/COM Port
- Parallel Port
- VT-d (can be enabled if you set `DisableIoMapper` to YES)
- Compatibility Support Module (CSM).
- Thunderbolt(For initial install, as Thunderbolt can cause issues if not setup correctly)
- Intel SGX
- Intel Platform Trust
- CFG Lock (MSR 0xE2 write protection)
	- This must be off, if you can't find the option then **`ENABLE`** `AppleXcpmCfgLock`. 
	- Your hack will not boot with `CFG-Lock` enabled.

### Enable
- VT-x
- Above 4G decoding. 
	- This must be on, if you can't find the option then add `npci=0x2000` to `boot-args`. 
	- Do not have both this option and `npci` on `boot-args` enabled at the same time.
	- When enabling Above4G, Resizable BAR Support may become an available on some motherboards. Please ensure this is **`DISABLED`** instead of set to Auto.
- Hyper-Threading
- Execute Disable Bit
- EHCI/XHCI Hand-off
- OS type: Windows 8.1/10 UEFI Mode
- SATA Mode: AHCI
