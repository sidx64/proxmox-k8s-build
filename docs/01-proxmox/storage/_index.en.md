# Proxmox Storage Configuration

This section helps you to configure storage options correctly for the Proxmox setup. To host VM images, ISO files and similar assetsm, we need to configure storage correctly. We use ZFS file system for our proxmox VM disk image storage. The default local storage can be used to store the ISO images of various OSes that we import/upload on to Proxmox.

## Assumptions:

1. You have a disk partition created in your homelab machine (on Debian). This will be used to create the ZFS storage disk.

## Decide on storage size

The size of the ZFS volume depends on the requirements that you have, and how you intend to use Proxmox. I intend to create up to 6 VMs which will be used for various purposes, and to start with, I feel 512GB of storage is more than enough for my requirement (and then some).

## Create the ZFS Storage disk

1. Click on the Data Center Node and click on the Storage tab. Then click on "ZFS"

2. Give a logical name for the ZFS disk (I gave "proxmox-disk-1"), and select the right device that will be used to create this disk. Choose "zstd" as the compression method, and "Single Disk" as a RAID level. Note that ZFS is not compatible with disks backed by a hardware RAID controller. Then click "create".

3. Once created, the ZFS disk will show details similar to this: ![Permissions](../../assets/proxmox-disk.png?width=90pc)
