# RTL8188EUS Driver for Linux Kernel 6.14

This is a patched version of the `aircrack-ng/rtl8188eus` driver, specifically updated to support Linux Kernel **6.14.0-37-generic**.

## Patches Applied

1.  **Preprocessor Balancing**: Fixed a missing `#endif` in `os_dep/linux/ioctl_cfg80211.c` that caused structural corruption in the code on modern kernels.
2.  **API Compatibility**: Fixed several syntax typos (e.g., `chandef` -> `chdef`) and removed redundant registrations that caused "duplicate member" errors in `rtw_cfg80211_ops`.
3.  **Variable Shadowing**: Cleaned up uninitialized and undeclared variable usage in `ioctl_cfg80211.c`.

## Installation

### Prerequisites
You need the kernel headers and build tools installed:
```bash
sudo apt update
sudo apt install linux-headers-$(uname -r) build-essential dkms git
```

### via DKMS (Recommended)
```bash
sudo dkms add -m 8188eu -v 5.3.9
sudo dkms build -m 8188eu -v 5.3.9
sudo dkms install -m 8188eu -v 5.3.9
sudo modprobe 8188eu
```

### Manual Build
```bash
make
sudo make install
sudo modprobe 8188eu
```

## Credits
Based on the [aircrack-ng/rtl8188eus](https://github.com/aircrack-ng/rtl8188eus) repository.
