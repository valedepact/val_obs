# Common Issues & Fixes

## Ollama

```bash
sudo systemctl status ollama             # check if the ollama service is running
sudo systemctl restart ollama            # restart if it's stuck/unresponsive
curl http://localhost:11434              # test if the API is reachable (should respond, not connection refused)
sudo lsof -i :11434                      # find what's using the port if it won't start
```

## Obsidian (AppImage)

```bash
sudo apt install libfuse2 -y             # fixes "AppImage requires FUSE" error
chmod +x Obsidian.AppImage                # fixes "permission denied" on launch
./Obsidian.AppImage --no-sandbox          # fixes sandbox/chrome-sandbox launch errors on Linux
```

## VirtualBox

```bash
sudo usermod -aG vboxusers $USER          # fixes "not in vboxusers group" permission errors, then log out/in
sudo /sbin/vboxconfig                     # rebuilds kernel modules after a kernel update (fixes VM won't start)
sudo dpkg --configure -a                  # fixes broken dkms/module install after a failed apt run
VBoxManage list vms                       # confirms VMs are registered if GUI doesn't show them
```

## OpenVPN

```bash
sudo systemctl status openvpn-server@server   # check why the server isn't starting
sudo journalctl -u openvpn-server@server -e   # view detailed error logs
sudo ufw allow 1194/udp                       # fixes client can't connect (port blocked)
sudo sysctl net.ipv4.ip_forward               # should return 1; fixes clients connect but can't reach internet
sudo iptables -t nat -L -n                    # confirms NAT/MASQUERADE rule is present
```

---

# Desktop Environment Issues (GNOME & XFCE)

## GNOME

```bash
sudo apt install --reinstall gnome-shell -y   # fixes GNOME Shell crashing/freezing
killall -3 gnome-shell                        # restarts GNOME Shell without logging out (X11 only)
gnome-extensions list                         # fixes broken/missing extensions, lists installed ones
dconf reset -f /org/gnome/                    # resets GNOME settings to default if UI is broken
```

## XFCE

```bash
xfwm4 --replace &                             # restarts the XFCE window manager if it crashes
xfce4-panel -r                                # restarts a frozen/crashed panel
rm -rf ~/.cache/sessions/*                    # fixes XFCE failing to restore session on login
sudo apt install --reinstall xfce4-settings -y  # fixes broken settings manager
```

## Both (general display/session fixes)

```bash
sudo systemctl restart lightdm                # restarts the login/display manager (or gdm3/sddm depending on setup)
startx                                         # manually starts a session if the display manager fails
sudo dpkg-reconfigure xserver-xorg             # fixes broken X server config causing black screen
journalctl -b -p err                           # checks boot log for errors affecting desktop startup
```
