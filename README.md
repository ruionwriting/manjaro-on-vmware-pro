# Manjaro Linux On VMWare Pro 16

> Manjaro Linux developmento environment running on VMWare Pro 16 learning notes.

- [System Details](#system-details)
  - [Host](#host)
  - [Guest](#guest)
- [VMWare Pro 16](#vmware-pro-16)
  - [Troubleshooting](#troubleshooting)
- [Manjaro](#manjaro)
  - [ZSH (using Oh My ZSH)](#zsh-using-oh-my-zsh)
  - [Install Docker](#install-docker)
  - [Package management](#package-management)
    - [PacMan cheat-sheet](#pacman-cheat-sheet)
    - [Pamac](#pamac)
  - [Browsers](#browsers)
    - [Microsoft Edge](#microsoft-edge)
  - [Development](#development)
    - [Git: Signing commits](#git-signing-commits)
    - [Visual Studio Code](#visual-studio-code)
    - [Node.js](#nodejs)

## System Details

### Host

- Windows 11 Home 64-bit
- AMD Ryzen 7 5800X 8-Core Processor
- 32 GB RAM
- MOBO B550 AORUS ELITE AX V2 (AM4)
- NVIDIA GeForce GTX 1050 Ti

### Guest

- Manjaro Linux 64-bit
- 4/2 cores, total of 8 CPU cores
- RAM 16 GB
- SCSI 120 GB (prellocated)
- NAT network
- 3D graphics with 8 GB for graphics memory

## VMWare Pro 16

1. [Download VMware Workstation Pro](https://www.vmware.com/uk/products/workstation-pro/workstation-pro-evaluation.html)
2. Install and reboot

### Troubleshooting

**Issue**: `Workstation 15 Pro - Exception 0xc0000005 (access violation) has occurred` errors on VM or shutdown of your Linux VM.

Resolution:

- [VMware product unexpectedly fails with an unrecoverable error (1008485)](https://kb.vmware.com/s/article/1008485)
- What worked for me? [This solution](VMware product unexpectedly fails with an unrecoverable error (1008485)): Add `monitor_control.disable_apichv = "TRUE"` to the VM's _.vmx_ configuation file.

**Issue**: `Transport (VMDB) error -14: Pipe connection has been broken.` when taking a snapshot.

Resolution:

- From this [SO answer](https://stackoverflow.com/a/66975189)
- `Turn Windows Features on or off` and disable/uncheck:
  - Windows Subsystem for Linux
  - Hyper-V
  - Virtual Machine Platform
  - Windows Hipervisor Platform 
- Reboot

## Manjaro

> **Note**
> Take regular snapshots.

### ZSH (using Oh My ZSH)

[The setup I like to follow](https://gist.github.com/yovko/becf16eecd3a1f69a4e320a95689249e).

### Install Docker

Make sure Manjaro is up to date:

```shell
sudo pacman -Syu
```

Install Docker:

```shell
sudo pacman -S docker
```

Start Docker service:

```shell
sudo systemctl start docker.service
```

Enable on startup:

```shell
sudo systemctl enable docker.service
```

Check installation:

```shell
sudo docker version
```

or

```shell
sudo docker info
```

For development we would like to run Docker without root:

```shell
sudo usermod -aG docker $USER
```

Now we reboot:

```shell
reboot
```

References:

- [Docker](https://wiki.archlinux.org/title/docker) guide on archlinux wiki
- [Manjaro Linux Docker installation](https://linuxconfig.org/manjaro-linux-docker-installation)

### Package management

#### PacMan cheat-sheet

| Command | Descriptio |
|---|---|
| `sudo pacman -Syu` | Update system to latest version |

#### Pamac

Enables AUR packages and tweak settings. [follow](https://wiki.manjaro.org/index.php/Pamac) for full details.

Updating the System:

```shell
pamac checkupdates -a
```

Update all installed packages:

```shell
pamac upgrade -a
```

### Browsers

#### Microsoft Edge

```shell
pamac install microsoft-edge-beta-bin
```

### Development

#### Git: Signing commits

Follow [Generating a new GPG key](https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key).

[Signing commits](https://docs.github.com/en/authentication/managing-commit-signature-verification/signing-commits)

```shell
git config --global commit.gpgsign true
```

```shell
git config --global user.signingkey ***********8D9
```

#### Visual Studio Code

Arch [wiki](https://wiki.archlinux.org/title/Visual_Studio_Code#Installation) provides many options. I've used:

```shell
sudo pacman -Syu code
```

So we can get all package sources for extensions:

```shell
pamac install code-marketplace
```

#### Node.js

Follow [Node.js](NODEJS.md) guide.
