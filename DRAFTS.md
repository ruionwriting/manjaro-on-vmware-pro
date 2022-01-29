# Draft Notes

## Manjaro Installation

1. Boot the VM and press `Launch installer` when the welcome window is presented. The system will install
1. Update system to latest packages

   ```shell
   sudo pacman -Syu
   ```
  
1. Install [Open-VM-Tools](https://wiki.archlinux.org/title/VMware/Install_Arch_Linux_as_a_guest#VMware_Tools_versus_Open-VM-Tools)

   ```shell
   sudo pacman -S open-vm-tools
   ```
   
   Now using [Systemd](https://wiki.archlinux.org/title/Systemd#Using_units) we start and enable the service
   
   ```shell
   sudo systemctl enable --now vmtoolsd.service
   ```
   
   ```shell
   sudo systemctl enable --now vmware-vmblock-fuse.service
   ```
   
   Reboot. In case resolutions is still limited to 800x600 check [troubleshooting](https://wiki.archlinux.org/title/VMware/Install_Arch_Linux_as_a_guest#Window_resolution_autofit_problems) guide.

## Guides

1. [Pacman Guide](https://kaosx.us/docs/pacman/)
2. 
