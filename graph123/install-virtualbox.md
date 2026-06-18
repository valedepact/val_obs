# VirtualBox Installation

```bash
sudo apt update                          # refresh package lists
sudo apt install virtualbox virtualbox-qt virtualbox-dkms -y   # install VirtualBox + Qt UI + kernel module sources
sudo usermod -aG vboxusers $USER         # add current user to vboxusers group
VBoxManage --version                     # confirm install, check version
VBoxManage list vms                      # list existing virtual machines
```
