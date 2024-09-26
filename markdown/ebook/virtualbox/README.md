# VirtualBox

## Install

### Archlinux (`pacman`)

```bash
sudo pacman -Syu
sudo pacman -S virtualbox
```

### [Optional] Install Extension pack

[VirtualBox Extension Pack](https://www.virtualbox.org/wiki/Downloads) or [Preview VirtualBox Extension Pack](https://www.virtualbox.org/wiki/Download_Old_Builds)

```bash
VBoxManage extpack install Oracle_*_VirtualBox_Extension_Pack-version.vbox-extpack
```

#### Load the VirtualBox kernel modules (if not already loaded):

```bash
sudo modprobe vboxdrv
```

**[Optional]**

```bash
sudo modprobe vboxnetadp
sudo modprobe vboxnetflt
sudo modprobe vboxpci
```

To ensure these modules load automatically on boot, you can add them to the /etc/modules-load.d/virtualbox.conf file:

```bash
echo -e "vboxdrv\nvboxnetadp\nvboxnetflt\nvboxpci" | sudo tee /etc/modules-load.d/virtualbox.conf
```

#### **Add Your User to the vboxusers Group**

To allow your user to run VirtualBox, you need to add your user to the vboxusers group:

```bash
sudo usermod -aG vboxusers $(whoami)
```

After running this command, log out and log back in for the changes to take effect.
