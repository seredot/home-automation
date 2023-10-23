# Infrastructure installation
## Install VM
- Used Archlinux Linux VM image.
- Log into VM.

# Install Docker
pacman -S docker
systemctl start docker.service
systemctl status docker.service
systemctl enable docker.service
pacman -S git
