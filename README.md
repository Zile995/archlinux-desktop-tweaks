# archlinux-pop_os-config
Pop!_OS zRAM, virtual memory and IO scheduler configuration for Arch Linux

## Changes
  * Enabled one swap zRAM device with a size of:
    * Total system memory for PCs with less than 16GB of RAM
    * 16GB for PCs with more than 16GB of RAM
    
  * Sysctl vm tweaks:
    ```Shell
    vm.swappiness = 180
    vm.page-cluster = 0
    vm.watermark_boost_factor = 0
    vm.watermark_scale_factor = 125
    vm.dirty_bytes = 268435456
    vm.dirty_background_bytes = 134217728
    ```
  * Set the default IO schedulers:
    * `bfq` for HDD and SD cards
    * `kyber` for NVMe and SATA SSDs.

## Installation
  * Simply run this command:
    ```
    makepkg -si
    ```
  * Remember to disable `zswap` by adding `zswap.enabled=0` to the kernel parameters
  * If you have a swap partition, delete it. Also delete it from the `/etc/fstab` file.
