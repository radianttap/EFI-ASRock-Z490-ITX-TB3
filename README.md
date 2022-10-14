# EFI-ASRock-Z490-ITX-TB3

- OpenCore v0.8.5
- Monterey 12.6
- iMac20,1

## Hardware

Only the relevant parts:

* Intel [i7-10700K](https://ark.intel.com/content/www/us/en/ark/products/199335/intel-core-i7-10700k-processor-16m-cache-up-to-5-10-ghz.html) 3.8GHz 8-core CPU
* ASRock [Z490 Phantom Gaming ITX/TB3](https://www.asrock.com/mb/Intel/Z490%20Phantom%20Gaming-ITXTB3/index.asp) motherboard
* [NCASE M1](https://ncases.com/products/m1) V6.1 chassis (silver) with two front USB-A ports
* Corsair [Vengeance LPX 32GB](https://www.corsair.com/ww/en/Categories/Products/Memory/VENGEANCE-LPX/p/CMK32GX4M2D3200C16) DDR4 DRAM 3200MHz
* Sapphire [Nitro+ RX 5500 XT 8G SE](https://www.sapphiretech.com/en/consumer/nitro-radeon-rx-5500-xt-se-8g-gddr6) graphics card
* WD Blue [SN570](https://www.westerndigital.com/products/internal-drives/wd-blue-sn570-nvme-ssd#WDS100T3B0C) NVMe SSDs in 1TB (for macOS)
* [XPG 8200 Pro](https://www.xpg.com/us/feature/583/) NVMe SSD 512GB (for Windows)

### WiFI / Bt

The combo below offers natively supported WiFi 5 / Bluetooth 4.

- 1750Mbps Dual Band WiFi 2.4GHz/5GHz / Bluetooth 4.0 [Broadcom BCM94360CD](https://www.aliexpress.com/item/1750Mbps-Dual-Band-WiFi-Bluetooth-Card-2-4GHz-5GHz-BT-4-0-Broadcom-BCM94360CD-Wireless-Module/32974196141.html) card
- mini PCIe [adapter card](https://www.aliexpress.com/item/MINI-PCI-E-Adapter-Converter-to-wireless-wifi-card-BCM94360CD-BCM94331CD-BCM94360CS-BCM94360CS2-module-for-macbook/32256494722.html)

Combined with this riser cable, the card/adapter combo from above can be moved outside the motherboard I/O shroud, instead of existing Intel AX200 card.

- Mini [PCIe riser with adapter](https://www.aliexpress.com/item/BCM94360CD-BCM94360CS2-BCM943224PCIEBT2-Card-To-M-2-Key-A-E-Cable-For-Mac-OS-and-and/4000286967003.html) for M.2 Key A/E

This switch is fully compatible with Bluetooth capability in ASRock BIOS thus you can use Bluetooth keyboard for F2, F11 etc.

### BIOS

Version 1.40

## Usage

1. [Update `PlatformInfo/Generic` stuff](https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html#generate-a-new-serial) with your own, inside `config.plist`
2. Use your Ethernet’s MAC address for `ROM` value, as explained in the Dortania guide. Don’t leave it as all 0s.
3. Update value of `brcmfx-country` argument in `NVRAM/7C436110-AB2A-4BBB-A880-FE41995C9F82/boot-args` with your country code. Should be identical or compatible with what your WiFi router is broadcasting. (Remove the parameter if you don’t know what I’m talking about here.)
4. Turn off Power Nap in Energy Saver.

Important: Add `-v` boot-args parameter to get verbose boot process, it greatly simplifies troubleshooting.

### What’s working

Pretty much everything.

- NVMe SSD recognised properly.
- Radeon GPU, with properly boosted performance.
- WiFi, Bluetooth
- Ethernet (1 Gbps, when setup in macOS: see ETHERNET note in [Papadiche’s guide](https://www.reddit.com/r/hackintosh/comments/i3pega/z490_itx_guide/)).
- All media services (Plex, Netflix in Safari, iTunes, Apple TV+ etc). All are fully hardware-accelerated.
- 4K HDMI with HDR, Dolby.
- Watch unlock, Handoff, iMessage, iCloud, Keychain, Xcode etc.
- System Integrity Protection (SIP) fully enabled.
- Sleep / wake

### What’s not working

- Sidecar
- Thunderbolt 3 likely works but I have chosen to disable it. The .efi driver appeared in few kernel panics and since no TB3 device is used, it’s now off.

## Notes

Use at your own risk. 

- All `.efi` drivers and `.kext` are `-DEBUG` builds from the respective packages. 
- OpenCanopy (GUI boot menu) is up and running.
- I don’t boot Windows 10 using OC, thus I can’t guarantee it will work. I have Win 10 installed on separate SSD and switch using Boot Menu.

**Don’t ask me for help.** This stuff is finicky and so infuriatingly detailed that every little mis-step can be a proper headache. This is why [Dortania](https://dortania.github.io) advises to not reuse anyone’s EFI. At least not do it blindly without knowing where to look into. 

Ask [on reddit](https://www.reddit.com/r/hackintosh/) and the [discord server](https://discord.gg/Wxam8aH).

Good luck.

## Give back

If you found this code useful, please consider [buying me a coffee](https://www.buymeacoffee.com/radianttap) or two. ☕️😋
