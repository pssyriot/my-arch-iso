# Custom Arch Linux / EndeavourOS Offline ISO

This repository hosts a customized, offline-installable Arch Linux / EndeavourOS ISO image featuring a pre-configured **Hyprland + Quickshell** desktop environment and custom network scripts.

## How to Download and Assemble the ISO

Because GitHub Releases limits individual files to 2 GB, the ISO image is split into multiple volumes (`pssy-custom.iso.part_*`) along with a `checksum.sha256` verification file.

### 1. Download the Release Files
Download all `pssy-custom.iso.part_*` files and `checksum.sha256` from the [Latest Release](../../releases/latest) into a single directory, or use the GitHub CLI:

```bash
gh release download --repo pssyriot/my-arch-iso
```

### 2. Reassemble and Verify the Image
Open a terminal in the folder containing the downloaded files and run:

```bash
# Combine all parts into a single ISO file
cat pssy-custom.iso.part_* > pssy-custom.iso

# Verify file integrity (must output "OK")
sha256sum -c checksum.sha256
```

## Installation Notes

* **Bootable USB:** Copy the assembled `pssy-custom.iso` onto a [Ventoy](https://ventoy.net) USB drive or flash it directly using `dd` / Rufus.
* **BIOS Settings:** Ensure **Secure Boot** is disabled and boot mode is set to **UEFI**.
* **Live Environment Credentials:** Default live session user/password is `1234` / `1234`. Launch the system installer from the desktop/terminal (`sudo eggs sysinstall`) to create your own user and password.
* **VPN Configuration:** Personal VPN keys are stripped from this image. Add your own WireGuard / AmneziaWG peer configuration to `/etc/amnezia/amneziawg/client.conf` after installation.
