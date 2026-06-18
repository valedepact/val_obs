# OpenVPN Server Installation & Setup

```bash
sudo apt-get update                      # refresh package lists
sudo apt-get install openvpn -y          # install OpenVPN

sudo apt install easy-rsa -y             # install easy-rsa, used to build the CA/certs
make-cadir ~/openvpn-ca                  # create a CA directory
cd ~/openvpn-ca
./easyrsa init-pki                       # initialize the public key infrastructure
./easyrsa build-ca nopass                # build the Certificate Authority (no password)
./easyrsa gen-req server nopass          # generate server certificate request
./easyrsa sign-req server server         # sign the server certificate
./easyrsa gen-dh                         # generate Diffie-Hellman parameters

cd /etc/openvpn/server                   # location for server config and certs

sudo nano /etc/openvpn/server/server.conf   # create/edit server config:
# port 1194
# proto udp
# dev tun
# ca /etc/openvpn/server/ca.crt
# cert /etc/openvpn/server/server.crt
# key /etc/openvpn/server/server.key
# dh /etc/openvpn/server/dh.pem
# topology subnet
# server 10.8.0.0 255.255.255.0

sudo sysctl -w net.ipv4.ip_forward=1     # enable IP forwarding (runtime)
echo "net.ipv4.ip_forward=1" | sudo tee -a /etc/sysctl.conf   # persist IP forwarding on reboot

sudo iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE   # NAT so VPN clients reach the internet

sudo ufw allow 1194/udp                  # allow OpenVPN port through firewall

sudo systemctl start openvpn-server@server     # start the OpenVPN service
sudo systemctl status openvpn-server@server    # check it's running

sudo tail -f /var/log/openvpn.log        # monitor logs for errors

openvpn --config /path/to/client.ovpn    # (client side) connect using client config
```
