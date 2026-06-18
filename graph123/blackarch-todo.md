# BlackArch Setup To-Do (BlackArch already installed)

## 1. AI Automation (do this first)

```bash
sudo pacman -Syu                          # update system first
curl -fsSL https://claude.ai/install.sh | bash   # install Claude Code CLI (native installer)
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc   # ensure ~/.local/bin is on PATH
source ~/.bashrc
claude --version                          # confirm install
claude                                     # launch, then run /login to authenticate
```

```bash
sudo pacman -S python-pip                 # needed for SGPT
pip install shell-gpt --break-system-packages   # install SGPT (shell-gpt)
sgpt --version                            # confirm install
sgpt --api-key <YOUR_OPENAI_KEY>          # set API key (or export OPENAI_API_KEY=...)
```

- [ ] Claude Code CLI installed and logged in
- [ ] SGPT installed and API key configured
- [ ] Test a sample automation prompt (e.g. a scan/report task) to confirm it works end-to-end

## 2. Ollama

```bash
curl -fsSL https://ollama.com/install.sh | sh   # official install script (works on Arch too)
ollama --version
ollama pull llama3
ollama run llama3
```

- [ ] Ollama installed
- [ ] At least one model pulled and running

## 3. Obsidian (AppImage)

```bash
sudo pacman -S fuse2                      # dependency for AppImage
mkdir -p ~/Applications
cd ~/Applications
wget https://github.com/obsidianmd/obsidian-releases/releases/latest/download/Obsidian-1.x.x.AppImage -O Obsidian.AppImage
chmod +x Obsidian.AppImage
./Obsidian.AppImage
```

- [ ] Obsidian installed and vaults synced from GitHub (val_obs repo)

## 4. VirtualBox

```bash
sudo pacman -S virtualbox virtualbox-host-modules-arch virtualbox-guest-iso
sudo modprobe vboxdrv                     # load the kernel module
sudo usermod -aG vboxusers $USER          # add user to vboxusers group, then log out/in
VBoxManage --version
```

- [ ] VirtualBox installed, kernel module loads
- [ ] VMs recreated/imported as needed

## 5. OpenVPN

```bash
sudo pacman -S openvpn easy-rsa
make-cadir ~/openvpn-ca
cd ~/openvpn-ca
./easyrsa init-pki
./easyrsa build-ca nopass
./easyrsa gen-req server nopass
./easyrsa sign-req server server
./easyrsa gen-dh

# server.conf, IP forwarding, NAT/iptables, and systemd service steps
# are the same as documented in install-openvpn.md
```

- [ ] OpenVPN + easy-rsa installed
- [ ] Server cert/key/dh generated
- [ ] server.conf written, IP forwarding + NAT configured
- [ ] Service starts and a client can connect

## 6. SSH key for GitHub (if pushing notes from this machine too)

```bash
ssh-keygen -t ed25519 -C "your_email@example.com" -f ~/.ssh/id_ed25519_github -N ""
cat ~/.ssh/id_ed25519_github.pub          # paste into GitHub deploy keys / SSH keys
```

If port 22 is blocked, add to `~/.ssh/config`:
```
Host github.com
  HostName ssh.github.com
  Port 443
  User git
  IdentityFile ~/.ssh/id_ed25519_github
  IdentitiesOnly yes
```

- [ ] SSH key generated and added to GitHub
- [ ] Test push/pull works
