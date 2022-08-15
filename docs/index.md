# About the initiative

## The idea

With the single intent of learning the working and internals of Kubernetes, I began dreaming of the idea of a HomeLab. This homelab would be a central location where I could run my various projects, and do a bit of prototyping as well as learning. To be able to run full-fledged Kubernetes Clusters, we would need a playground area where we could make and break the systems multiple times during the course of learning how it all works. So that's where our journey begins. This document intends to be a journal of sorts, a document of my learnings̵ if you will. Following the document step-by-step should also yield a fully functional kubernetes cluster on your home system.

## The hardware

While Kubernetes clusters can be built on top of considerably cheap and low-powered hardware, based on my needs and the future plans I had for my HomeLab, I decided to go with a beefed-up desktop workstation. I could also have gone with a used/refurbished DL360 Gen 8 server with Intel Xeon based processors, or gone the tiny PC route with the Intel NUC platform, but prospective noise and power bills put me off the server path. NUCs on the other hand, seem to be pretty highly priced at the moment, and are hard to procure too. Hence, I zeroed-in on the following configuration:

| Component  | Configuration/Capacity                       | Comments                                                                                                                                     |
| ---------- | -------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| Processor  | AMD Ryzen 9 5950x                            | With 16 cores and 32 threads in total, this is the best-in-class processor today, second only to the AMD threadripper series.                |
| RAM        | G.Skill RipJaws 2x32G DDR4 3600MHz           | It is recommended to go with a 3600MHz RAM cards in order to make the best use of the Ryzen 5000 series processors.                          |
| Mainboard  | Asus TUF x570 Mainboard                      | We needed a mainboard that supports the AM4 processor platform, and has enough slots to support at least two SSD nVME cards.                 |
| Storage    | Western Digital SN850 Black 1TB+2TB SSD nVME | With 7000MBps Read and 4100MBps Write speeds, this is an excellent candidate for what we intend to do.                                       |
| Graphics   | Asus NVidia GT730 2GB                        | We dont really need a heavy Graphics solution for this, so we went with a simple 2GB NVidia GT730 based graphics solution.                   |
| Networking | Intel i350 T2 Gigabit Ethernet Card          | The Asus x570 Mainboard comes with a Realtek based network card, and since I needed dual ports, the Intel i350 seemed to be the best choice. |

## The setup

With the compute config laid out above, I went ahead with the following configuration for our setup:
![Infrastructure Setup](../assets/IMG_0129.JPG?width=90pc)

The image above represents the setup I decided to go with:

1. We dual-boot the host machine with Windows 11 and Debian 11 Linux (the Windows11 system is just there for windows-related personal work I may come accross).

2. The Debian system runs Proxmox - a type 1 Hypervisor. Proxmox allows us to build our virtual machines, containers, and more in a datacenter-like fashion.

3. Within Proxmox, we then build virtual nodes that will act as Kubernetes cluster members that will run our containerised workloads.

## The goal

1. Setup a quick infrastructure automation framework that can quickly let us build the Kubernetes Cluster nodes, and have Kubernetes setup in a fully automated fashion using Terraform.

2. Use the Kubernetes Cluster to run some containerised workloads.

3. Use the kubernetes cluster to prepare and ready myself for the upcoming CKAD certification.
