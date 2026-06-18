**What it is**: A self-hosted OpenVPN server running on this Kali machine, using your own Certificate Authority (created with easy-rsa) rather than a commercial one. The server listens on UDP port 1194 and creates a virtual private network (10.8.0.0/24), with this machine acting as the gateway at 10.8.0.1 on a virtual `tun0` interface.

**How it works**: OpenVPN authenticates using certificates rather than just passwords. Your CA cert (`ca.crt`) is the root of trust — the server has its own certificate signed by that CA, and each client (like `client1`) gets its own certificate, also signed by the same CA. When a client connects using `client1.ovpn`, it presents its certificate, the server checks it was signed by your CA, and an encrypted tunnel is established over UDP. Because the config includes `redirect-gateway`, once connected, all of that client's internet traffic routes through this Kali machine.

**How to use it**: copy `client1.ovpn` to any device, run `sudo openvpn --config client1.ovpn`, and that device's traffic now tunnels through this server.

**Where/when it works**: this Kali machine has a private IP (10.10.2.103) behind your router's NAT, so the server is only reachable from devices on the same local network right now — not from the internet. It runs as long as the `openvpn-server@server` service is active (currently started, but not yet set to survive a reboot — run `sudo systemctl enable openvpn-server@server` if you want it persistent). To make it reachable remotely, you'd need port forwarding on your router (UDP 1194 → this machine) plus a public IP or dynamic DNS.

**Why this matters / worth including**: this exercise covers core VPN concepts — PKI/certificate-based authentication, tunnel interfaces, NAT and IP forwarding, and routing — which ties into networking and cybersecurity fundamentals. Practically, it also gives you an encrypted tunnel any future VM in your sandbox can connect through.

**One gap worth noting**: no `tls-auth`/`tls-crypt` key was added, which is normally used as an extra hardening layer against scanning/DoS on the OpenVPN port. Good to mention as a "future improvement" if this is for an assignment.
