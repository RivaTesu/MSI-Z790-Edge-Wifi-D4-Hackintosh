# Hackintosh EFI - MSI Z790 Edge WiFi D4 + i7-13700K + RX 6800 XT

This is my fully working OpenCore EFI for macOS Sonoma 14.5 on an Intel 13th Gen platform with an AMD GPU.

---

## 🖥️ Hardware

| Component | Model |
|------------|----------------------------|
| Motherboard | MSI Z790 Edge WiFi D4 |
| CPU | Intel Core i7-13700K |
| GPU | Sapphire RX 6800 XT |
| RAM | 64 GB DDR4 XPG ROG Strix |

---

## ⚙ OpenCore

- **Version:** 1.0.5
- **Release date:** 07/07/2025

---

## 🧩 Kexts Included

The following kexts are included and configured for this setup:

- **AirportItlwm.kext** — Enables native Wi-Fi support for Intel wireless cards.  
- **AppleALC.kext** — Provides audio support by enabling native macOS audio codecs.  
- **AppleIGC.kext** — Supports Intel Ethernet controllers for network connectivity.  
- **BlueToolFixup.kext** — Fixes Bluetooth issues on Intel platforms.  
- **CpuTopologyRebuild.kext** — Corrects CPU core and thread reporting for better power management.  
- **CpuTscSync.kext** — Synchronizes CPU time stamp counters to fix multi-core timing issues.  
- **FeatureUnlock.kext** — Unlocks hidden CPU features for improved performance.  
- **IntelBluetoothFirmware.kext** — Loads firmware for Intel Bluetooth devices.  
- **IntelBTPatcher.kext** — Patches Intel Bluetooth for proper functionality on macOS.  
- **Lilu.kext** — Framework kext that provides patching capabilities for other kexts.  
- **NVMeFix.kext** — Improves NVMe SSD compatibility and performance on macOS.  
- **RestrictEvents.kext** — Helps fix issues related to USB and other device events.  
- **SMCProcessor.kext** — Emulates CPU sensors for macOS System Management Controller (SMC).  
- **SMCSuperIO.kext** — Emulates sensors from Super I/O chips for hardware monitoring.  
- **USBWakeFixup.kext** — Fixes USB wake issues to prevent system crashes or freezes.  
- **VirtualSMC.kext** — Essential virtual SMC implementation for Hackintosh systems.  
- **WhateverGreen.kext** — Fixes graphics issues and enables GPU acceleration on macOS.
- **Phantom.kext** — Circumvents software checks to make macOS appear as a genuine Macintosh.


---

## ✅ ACPI Tables

All ACPI tables are custom-generated for this hardware:
- DMAR.aml
- SSDT-EC.aml
- SSDT-GPRW.aml
- SSDT-HPET.aml
- SSDT-PLUG-ALT.aml
- SSDT-RTCAWAC.aml
- SSDT-SBUS.aml
- SSDT-USB-Reset.aml
- SSDT-USBW.aml
- SSDT-USBX.aml

---

## 🔑 BIOS Settings

### Disabled
- Fast Boot
- Secure Boot
- VT-d (optional, as `DisableIoMapper` is set to `True` in config.plist)
- Intel Platform Trust
- CFG Lock (MSR 0xE2 write protection)
- Hyper-Threading
- Resizable BAR
- E-Cores `Per E-Core Control` must be set to `Enabled And Dis All E-Core`

### Enabled
- Above 4G Decoding  
  ⚠ When enabling Above 4G Decoding, make sure Resizable BAR is **disabled** (not Auto).

---

## ⚡ Post-install tweaks

Run these commands after the first boot:

sudo pmset autopoweroff 0  
sudo pmset powernap 0  
sudo pmset standby 0  
sudo pmset proximitywake 0  
sudo pmset tcpkeepalive 0  

These settings:  
- Disable autopoweroff: Prevents hibernation-related wake issues  
- Disable powernap: Prevents periodic network wakeups  
- Disable standby: Prevents transition to hibernation after sleep  
- Disable proximity wake: Prevents wake triggered by nearby iPhone / Apple Watch  
- Disable TCP Keep Alive: Prevents wake-ups every 2 hours due to network  

---

## 💡 Notes

- macOS version: **Sonoma 14.5 (Olarila image)**
- Resizable BAR must remain **disabled**
- iMacPro1,1 SMBIOS is used for better stability on this setup
- OpenCore boot-args include:  
  keepsyms=1 debug=0x100 agdpmod=pikera revpatch=sbvmm -v -ctrsmt  
- The `SecureBootModel` is set to `Disabled` by default for installation ease and compatibility. You may enable it to `Default` after installation for improved security and system integrity.

---

## 📌 Disclaimer

This EFI is provided as-is for educational purposes.  
Please ensure you generate your own serials for `PlatformInfo` before use.

---

## 📝 Credits

- Dortania OpenCore Install Guide
- Olarila macOS resources
- Hackintosh community contributors
