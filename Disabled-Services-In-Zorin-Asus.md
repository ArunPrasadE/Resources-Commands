---
tags:
  - linux
  - command-list
---

# Complete Guide: CUPS and Avahi-Daemon

When hardening your Linux system for privacy, you may be prompted to disable certain background services. This guide explains what these two common services do, whether you actually need them, and how to turn them back on if you ever change your mind.

---

## 1. CUPS (Common UNIX Printing System)

**What is it?**
CUPS is the software layer that runs in the background and allows your Linux computer to communicate with physical printers.

**Do you need it?**
* **NO:** If you never print physical documents from this computer. (Note: "Print to PDF" will still work perfectly fine without CUPS).
* **YES:** If you connect to a physical printer via USB, or print to a wireless/network printer in your home or office.

**How to manage CUPS:**
If you disabled it during the privacy setup but need to print something later, you can instantly turn it back on with this command:
```bash
sudo systemctl enable --now cups
```
*(If you want to turn it back off after you finish printing, just change `enable` to `disable` in the command).*

---

## 2. Avahi-Daemon (Network Discovery)

**What is it?**
Avahi is Linux's network discovery tool (very similar to Apple's "Bonjour"). It continuously broadcasts your computer's presence to other devices on your local Wi-Fi network.

**Do you need it?**
* **NO:** If you take your laptop on public Wi-Fi (coffee shops, airports), or if you just browse the web and don't interact with other smart devices. Disabling it makes your computer "invisible" to strangers on the network.
* **YES:** If you are on a trusted home network and need to cast videos to a smart TV, find a network printer, or connect to shared network folders (like a NAS drive).

**How to manage Avahi-Daemon:**
If you disabled it but need to cast to a TV or find a network drive, turn it back on with:
```bash
sudo systemctl enable --now avahi-daemon
```