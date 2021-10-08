# Manjaro Linus On VMWare Pro 16

> Manjaro Linux developmento environment running on VMWare Pro 16 learning notes.

## System Details

### Host

* Windows 11 Home 6-bit
* AMD Ryzen 7 5800X 8-Core Processor
* 32 GB RAM
* MOBO B550 AORUS ELITE AX V2 (AM4)
* VIDIA GeForce GTX 1050 Ti

### Guest

* Manjaro Linux 64-bit
* 4/2 cores, total of 8 CPU cores
* RAM 16 GB
* SCSI 120 GB (prellocated)
* NAT network
* 3D graphics with 8 GB for graphics memory

## VMWare Pro 16

1. [Download VMware Workstation Pro](https://www.vmware.com/uk/products/workstation-pro/workstation-pro-evaluation.html)
2. Install and reboot

### Troubleshooting

**Issue**: `Workstation 15 Pro - Exception 0xc0000005 (access violation) has occurred` errors on VM or shutdown of your Linux VM.

Resolution:

* [VMware product unexpectedly fails with an unrecoverable error (1008485)](https://kb.vmware.com/s/article/1008485)
* What worked for me? [This solution](VMware product unexpectedly fails with an unrecoverable error (1008485)): Add `monitor_control.disable_apichv = "TRUE"` to the VM's _.vmx_ configuation file.

**Issue**: `Transport (VMDB) error -14: Pipe connection has been broken.` when taking a snapshot.

Resolution:

* From this [SO answer](https://stackoverflow.com/a/66975189)
* `Turn Windows Features on or off` and disable/uncheck:
   * Windows Subsystem for Linux
   * Hyper-V
   * Virtual Machine Platform
   * Windows Hipervisor Platform 
 * Reboot
