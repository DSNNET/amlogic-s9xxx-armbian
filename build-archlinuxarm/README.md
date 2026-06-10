# Arch Linux ARM Image Builder

This directory contains the Arch Linux ARM backend used by `rebuild-arch`.

Phase 1 scope is intentionally small:

- Default target: `Beelink-Mini-MX-2G` (`BOARD=s905-beelink-mini`).
- Use `ArchLinuxARM-aarch64-latest.tar.gz` as the rootfs.
- Reuse the existing model database, Amlogic bootfs templates, u-boot overload files, DTBs, and ophub kernel tarballs.
- Install ophub kernel files into `/boot` and `/usr/lib/modules`.
- Add `/etc/ophub-release`.
- Add `IgnorePkg` for Arch Linux ARM kernel packages so `pacman -Syu` does not replace the boot kernel.
- Enable SSH and wired DHCP through systemd-networkd.

Example:

```bash
sudo ./rebuild-arch
```

Use a local rootfs tarball:

```bash
sudo ./rebuild-arch -f build-archlinuxarm/rootfs/ArchLinuxARM-aarch64-latest.tar.gz
```

Build a specific kernel version:

```bash
sudo ./rebuild-arch -k 6.12.69
```
