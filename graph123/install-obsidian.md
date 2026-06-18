# Obsidian Installation (AppImage)

```bash
sudo apt update                          # refresh package lists
sudo apt install libfuse2 -y             # dependency needed to run AppImages
mkdir -p ~/Applications                  # folder to keep AppImages
cd ~/Applications
wget https://github.com/obsidianmd/obsidian-releases/releases/latest/download/Obsidian-1.x.x.AppImage -O Obsidian.AppImage   # download Obsidian
chmod +x Obsidian.AppImage               # make it executable
./Obsidian.AppImage                      # launch Obsidian
```
