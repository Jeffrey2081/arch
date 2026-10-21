# 🏹 Automated Arch Linux Server & Desktop Installer

An automated Arch Linux installation script designed to take a bare-metal machine or virtual machine from the live Arch ISO environment to a fully operational, customized Arch system with LUKS disk encryption, Btrfs/Ext4, optimized pacman mirrors, GRUB theme, and post-installation BSPWM desktop environment.

---

## 🚀 Features

- **Automated ISO Verification**: Checks if booted inside live Arch ISO with `pacstrap` available.
- **Disk Partitioning & Filesystems**:
  - Support for Standard `ext4` or encrypted `LUKS` root partitions.
  - Automatic EFI boot partition creation and formatting.
  - Swap partition or dynamic swapfile generation.
- **Hardware & Driver Detection**:
  - Auto-detection for CPU architecture (AMD / Intel microcode).
  - Dedicated graphics driver installation for NVIDIA, AMD Radeon, and Intel UHD graphics.
- **Performance Optimization**:
  - Automatically tunes `makepkg.conf` with multi-threaded compilation (`-j$(nproc)`) and multi-core `xz` compression based on installed RAM and CPU core count.
  - Optimizes `mirrorlist` with `reflector`.
- **Bootloader & Aesthetic**:
  - Configures GRUB with CyberRe theme and silent splash screen parameters.
- **Post-Install Integration**:
  - Clones and executes `arch-bspwm` desktop configuration for the created user.

---

## 🛠️ Usage

From an Arch Linux Live ISO environment:

```bash
# 1. Connect to Internet (Wi-Fi or Ethernet)
iwctl # if Wi-Fi

# 2. Download and run the installer
curl -sL https://raw.githubusercontent.com/Jeffrey2081/arch/main/server-setup.sh -o setup.sh
chmod +x setup.sh
./setup.sh
```

---

## 🛡️ Error Prevention & Improvements
- Fixed unclosed heredoc syntax error at the end of the chroot configuration block.
- Added graceful user fallback when invoking post-install scripts.
- Log capture into `archsetup.txt` while maintaining active terminal output.
