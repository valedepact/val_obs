while using gnome, the session is wayland, so we can't connect to the linux pc and see full screen due to wayland.

The remote machine you're connecting _to_ is a Linux box running **Wayland** as its display server, and AnyDesk can't capture or control a Wayland desktop. Wayland's security model deliberately stops applications from grabbing the whole screen or injecting mouse/keyboard input, which is exactly what a remote-desktop tool needs to do. So the session connects, AnyDesk tries to start screen capture, fails because it's Wayland, and the link aborts

The fix has to be done on the **remote** machine (the one being controlled), two ways:

**Quick, per-session:** At that machine's login screen, click the username, look for a small gear/settings icon in the corner, and choose the session labeled something like "Ubuntu on Xorg" or "GNOME on Xorg" (anything _without_ Wayland) before typing the password. This switches just that login. The downside is it doesn't survive every reboot and doesn't fix the login-screen greeter.

**Permanent:** Edit the display manager config and force Xorg. On most systems using GDM (Ubuntu, Fedora), open the config as root — `/etc/gdm3/custom.conf` on Debian/Ubuntu, or `/etc/gdm/custom.conf` on Fedora/RHEL — find the line `#WaylandEnable=false`, remove the `#` to uncomment it, save, and reboot. That puts both the greeter and the session on Xorg, so AnyDesk works for attended and unattended access. If the remote uses a different display manager (LightDM, SDDM), it's likely already on Xorg, so check which one it runs.