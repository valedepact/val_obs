we install GNOME desktop environment
1. Update system
`sudo apt update && sudo apt upgrade -y`
2. install gnome metapackage
`sudo apt install kali-desktop-gnome -y`
3. Select display manager
Highlight and choose **`gdm3`**
4. set up as default
`sudo update-alternatives --config x-session-manager`
Type the selection number that corresponds to `/usr/bin/gnome-session` and hit **Enter**.
5. reboot
6. select GNOME at login