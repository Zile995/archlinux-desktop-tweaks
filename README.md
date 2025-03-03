# archlinux-desktop-tweaks
zRAM, virtual memory, IO scheduler and various Arch Linux desktop tweaks.

## Changes
  * Enabled one swap zRAM device with a size of:
    * Total system memory for PCs with less than 16GB of RAM
    * 16GB for PCs with more than 16GB of RAM
 
  * Pop!_OS sysctl vm tweaks:
    ```Shell
    vm.swappiness = 180
    vm.page-cluster = 0
    vm.watermark_boost_factor = 0
    vm.watermark_scale_factor = 125
    vm.dirty_bytes = 268435456
    vm.dirty_background_bytes = 134217728
    ```
  * Pop!_OS IO schedulers tweaks, set the default IO schedulers:
    * `bfq` for HDD and SD cards
    * `kyber` for NVMe and SATA SSDs.
  * Set MGLRU `min_ttl_ms` to 1000ms
  * Faster Shutdown and Reboot times
    ```
    [Manager]
    DefaultTimeoutStopSec=10s
    ```

## Installation
  * Simply run this command:
    ```
    makepkg -si
    ```
  * Remember to disable `zswap` by adding `zswap.enabled=0` to the kernel parameters
  * If you have a swap partition, delete it. Also delete it from the `/etc/fstab` file.
