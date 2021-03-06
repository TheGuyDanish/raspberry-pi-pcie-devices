The Raspberry Pi Compute Module 4 IO Board exposes the Pi's PCI Express 1x lane directly on the board:

<img src="{{ site.url }}/images/cm4-io-board-pcie-slot.jpeg" style="display: block; margin: auto;" width="595" height="300" />

I'm on a mission to test out these and _many_ more PCIe cards on the Pi, and see what works, what doesn't, and what I can learn.

<img src="{{ site.url }}/images/cm4-pcie-cards.jpeg" style="display: block; margin: auto;" width="600" height="390" />

Below is a listing of _all_ the PCIe devices I've tested so far.

I post videos with a lot more detail for many of the devices, like my [Raspberry Pi Compute Module 4 Review](https://www.jeffgeerling.com/blog/2020/raspberry-pi-compute-module-4-review) and more on my [YouTube channel](https://www.youtube.com/c/JeffGeerling).

[This project is on GitHub](https://github.com/geerlingguy/raspberry-pi-pcie-devices), and you can follow along with the testing or suggest new things to test there.

## Categories
{: .no_toc}

- TOC
{:toc}

### GPUs (Graphics Cards)

| Device | Functionality | Driver required? | Notes |
| ------ | ------------- | ---------------- | ----- |
| [Zotac GeForce GT 710 1GB PCIe x1](https://amzn.to/3mdy1LE) | None | Yes | Drivers for ARM: [32-bit](https://www.nvidia.com/en-us/drivers/unix/linux-arm-display-archive/), [64-bit](https://www.nvidia.com/en-us/drivers/unix/linux-aarch64-archive/). Nouveau driver requires compilation. Requires extra [BAR space](https://gist.github.com/geerlingguy/9d78ea34cab8e18d71ee5954417429df). More details: [Issue #2](https://github.com/geerlingguy/raspberry-pi-pcie-devices/issues/2). |
| [VisionTek Radeon 5450 1GB PCIe x16](https://amzn.to/2Hh6KcI) | None | Yes | Needs [x1 to x16 cable](https://amzn.to/2ThfzFD). Radeon driver requires compilation (incompatible with amdgpu). Requires extra [BAR space](https://gist.github.com/geerlingguy/9d78ea34cab8e18d71ee5954417429df). More details: [Issue #4](https://github.com/geerlingguy/raspberry-pi-pcie-devices/issues/4). |
| [Sapphire Radeon RX 550 2GB PCIe x16](https://amzn.to/34vadwW) | [Currently Testing](https://github.com/geerlingguy/raspberry-pi-pcie-devices/issues/6)) | Yes | Needs [x1 to x16 powered adapter](https://amzn.to/3dZQM2u). AMDGPU driver requires compilation. Requires extra [BAR space](https://gist.github.com/geerlingguy/9d78ea34cab8e18d71ee5954417429df). More details: [Issue #6](https://github.com/geerlingguy/raspberry-pi-pcie-devices/issues/6).
| [EVGA GeForce GTX 750 Ti](https://amzn.to/3l2rrXs) | [Currently Testing](https://github.com/geerlingguy/raspberry-pi-pcie-devices/issues/26) | Yes | Needs [x1 to x16 powered adapter](https://amzn.to/3dZQM2u). Nouveau driver requires compilation. Requires extra [BAR space](https://gist.github.com/geerlingguy/9d78ea34cab8e18d71ee5954417429df). More details: [Issue #26](https://github.com/geerlingguy/raspberry-pi-pcie-devices/issues/26).

### USB cards

| Device | Functionality | Driver required? | Notes |
| ------ | ------------- | ---------------- | ----- |
| [Syba SD-PEX20199 PCIe x1 USB 3.1 & 3.0 adapter](https://amzn.to/31yArwD) | Full | No | N/A |
| [Inateck PCIe x1 USB 3.0 adapter](https://amzn.to/3oplt67) | Limited | No | Sometimes mounted devices at 5 Gbps, other times at 480 Mbps. |
| [A ADWITS PCIe 1x 'PCI Experss' USB 3.0 adapter with VL805](https://amzn.to/37CKTHr) | Limited | No | Sometimes mounted devices at 5 Gbps, other times at 480 Mbps. Requires external [5v DC 4-pin Molex power supply](https://amzn.to/37Cy0NA). |

### NVMe adapters

| Device | Functionality | Driver required? | Notes |
| ------ | ------------- | ---------------- | ----- |
| [NGFF M.2 M Key SSD to PCIe 1x Adapter](https://amzn.to/37tfWW1) | Full | No | Tested with [Samsung 970 EVO Plus](https://amzn.to/3mfJM4a). |
| [MZHOU NVMe M.2 SSD M Key to PCIe 1x Adapter](https://amzn.to/3maJ6NF) | Full | No | Tested with [Samsung 970 EVO Plus](https://amzn.to/3mfJM4a). |
| [Xiwai NGFF M Key M.2 SSD to PCIe 1x Adapter](https://amzn.to/3ogoQvL) | Full | No | Tested with [Samsung 970 EVO Plus](https://amzn.to/3mfJM4a). |

### Network cards (NICs)

| Device | Functionality | Driver required? | Notes |
| ------ | ------------- | ---------------- | ----- |
| [ASUS XG-C100C 10G Network Adapter](https://amzn.to/38wYOiL) | Currently Testing | Maybe | More details: [Issue #15](https://github.com/geerlingguy/raspberry-pi-pcie-devices/issues/15). |
| [EDUP PCIe Intel AX200 WiFi 6 Adapter](https://amzn.to/3pnFF8S) | Currently Testing | Maybe | More details: [Issue #22](https://github.com/geerlingguy/raspberry-pi-pcie-devices/issues/22). |
| [Mellanox ConnectX-2 MNPA19-XTR SFP+ 10G Ethernet Adapter]() | Currently Testing | Maybe | More details: [Issue #21](https://github.com/geerlingguy/raspberry-pi-pcie-devices/issues/21). |
| [Intel I340-T4 PCIe x4 4-port Gigabit Network Adapter](https://amzn.to/37vHQR6) | Full | Yes | Requires installation of [Intel Linux base driver](https://www.intel.com/content/www/us/en/support/articles/000005480/network-and-i-o/ethernet-products.html). PCIe lane limits to ~3.2 Gbps total bandwidth. More details: [Issue #3](https://github.com/geerlingguy/raspberry-pi-pcie-devices/issues/3). |
| [ASUS PCE-AC51 802.11ac WiFi Adapter](https://amzn.to/3ldzLVn) | Currently Testing | Maybe | More details: [Issue #20](https://github.com/geerlingguy/raspberry-pi-pcie-devices/issues/20). |

### SATA cards and storage

| Device | Functionality | Driver required? | Notes |
| ------ | ------------- | ---------------- | ----- |
| [IO Crest 4 Port SATA III PCIe x1 with Marvell 9215](https://amzn.to/2HpEWCP) | Full | Yes | Requires kernel recompile with `CONFIG_ATA` and `CONFIG_SATA_AHCI`. More details: [Issue #1](https://github.com/geerlingguy/raspberry-pi-pcie-devices/issues/1). |
| [IBM ServeRAID BR10i / LSI SAS3082E-R SAS RAID controller](https://amzn.to/2GVMZae) | Currently Testing | Maybe | Having trouble initializing. More details: [Issue #18](https://github.com/geerlingguy/raspberry-pi-pcie-devices/issues/18). |

### PCIe Switches and Adapters

| Device | Functionality | Driver required? | Notes |
| ------ | ------------- | ---------------- | ----- |
| [I/O Crest SI-PEX60016 1 to 2 Port PCIe Switch](https://amzn.to/2Ie0bI3) | Full | No | More details: [Issue #14](https://github.com/geerlingguy/raspberry-pi-pcie-devices/issues/14). |
| [HLT PCIe 1x to 16x extension cable](https://amzn.to/32oz9ou) | Full | No | More details: [Issue #14](https://github.com/geerlingguy/raspberry-pi-pcie-devices/issues/14). |
| [Rosewill RCRC-17001 Mining Card 1x to 16x](https://www.newegg.com/p/N82E16812119888?Item=9SIA85VAN30509) | None | No | More details: [Issue #14](https://github.com/geerlingguy/raspberry-pi-pcie-devices/issues/14). |

## About
{: .no_toc}

[![GitHub Stats](https://github-readme-stats.vercel.app/api/pin?username=geerlingguy&repo=raspberry-pi-pcie-devices&show_icons=true&hide_border=true&show_owner=true&theme=graywhite)](https://github.com/geerlingguy/raspberry-pi-pcie-devices)

This project is maintained by [Jeff Geerling](https://www.jeffgeerling.com). The Raspberry Pi Compute Module 4 is a product of [Raspberry Pi (Trading) Limited](https://www.raspberrypi.org/about/).

> Many of the device links on this page are Amazon affiliate links. If you do not wish to use those links, copy the device name to search for it at any major electronics retailer (e.g. [Newegg](https://www.newegg.com), [Micro Center](https://www.microcenter.com), [Amazon](https://www.amazon.com), etc.).
