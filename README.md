# wz_mini_hacks (USB Ethernet Focused)

This fork is intentionally scoped to one use case: running Wyze/Atomcam T20/T31 devices with a USB Ethernet adapter.

## What this fork keeps

- USB Ethernet adapter support (`ENABLE_USB_ETH`)
- Ethernet module auto-detect and optional manual module list
- Interface handoff so camera services continue to use `wlan0`
- Core boot/swap/firmware-intercept behavior needed for stable operation

## Configuration

Edit:

- `/opt/wz_mini/wz_mini.conf` on device
- `SD_ROOT/wz_mini/wz_mini.conf` in this repository

Primary settings:

- `ENABLE_USB_ETH="true"`
- `ENABLE_USB_ETH_MODULE_AUTODETECT="true"`
- `ENABLE_USB_ETH_MODULE_MANUAL=""` (comma-separated module names without `.ko` when needed)
- `USB_ETH_MAC_ADDR=""` (optional override)
- `CUSTOM_HOSTNAME="WCV3"` (optional hostname)

## Safety

Use at your own risk. Unsupported system modifications can brick devices.

## Additional docs

- `documentation/usb-ethernet.md`

## Recompilation Notes

Most day-to-day changes in this repo are text-only (for example `wz_mini.conf` and `etc/init.d/` scripts), so no recompilation is required. Copy the updated files to the SD card and reboot.

`generate_checksum.sh` only refreshes release checksum metadata (`file.chk`/`app.ver`) and does not compile binaries.

Kernel modules in `SD_ROOT/wz_mini/lib/modules/` are prebuilt (`.ko`). Recompilation is only needed if you choose to replace or rebuild those modules yourself with an external toolchain.
