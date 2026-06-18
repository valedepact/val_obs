$ pwsh
/usr/share/kali-menu/exec-in-shell: 1: eval: pwsh: not found
┌──(kali㉿kali)-[~]
└─$ cp /usr/share/applications/obsidian.desktop ~/Desktop/
cp: cannot stat '/usr/share/applications/obsidian.desktop': No such file or directory
                                                                             
┌──(kali㉿kali)-[~]
└─$ ls /var/lib/flatpak/exports/share/applications/ *obsidian* 2>/dev/null || ls ~/.local/share/applications/ *obsidian* 2>/dev/null
/home/kali/.local/share/applications/:
claude-code-url-handler.desktop  mimeinfo.cache
claude-desktop.desktop           obsidian.desktop
                                                                             
┌──(kali㉿kali)-[~]
└─$ cp ~/.local/share/applications/obsidian.desktop ~/Desktop/
                                                                             
┌──(kali㉿kali)-[~]
└─$ chmod +x ~/Desktop/obsidian.desktop
                                                                             
┌──(kali㉿kali)-[~]
└─$ ls ~/Desktop/*claude*
ls: cannot access '/home/kali/Desktop/*claude*': No such file or directory
                                                                             
┌──(kali㉿kali)-[~]
└─$ ls -l ~/.local/share/applications/ | grep claude
-rw-rw-r-- 1 kali kali 223 Jun 13 03:40 claude-code-url-handler.desktop
-rw-rw-r-- 1 kali kali 190 Jun 16 03:54 claude-desktop.desktop
                                                                             
┌──(kali㉿kali)-[~]
└─$ cp ~/.local/share/applications/claude-desktop.desktop ~/Desktop/
                                                                             
┌──(kali㉿kali)-[~]
└─$ chmod +x ~/Desktop/claude-desktop.desktop
                                                                             
┌──(kali㉿kali)-[~]
└─$ ls -l /usr/share/applications/ | grep -i virtualbox
-rw-r--r-- 1 root root  1029 Apr 28 03:44 virtualbox.desktop
                                                                             
┌──(kali㉿kali)-[~]
└─$ cp /usr/share/applications/virtualbox.desktop ~/Desktop/
                                                                             
┌──(kali㉿kali)-[~]
└─$ chmod +x ~/Desktop/virtualbox.desktop
                                                                             
┌──(kali㉿kali)-[~]
└─$ chmod +x ~/Desktop/virtualbox.desktop
                                                                             
┌──(kali㉿kali)-[~]
└─$ ls -l /usr/share/applications/ | grep -i firefox
-rw-r--r-- 1 root root  3826 May 19 18:48 firefox-esr.desktop
                                                                             
┌──(kali㉿kali)-[~]
└─$ cp /usr/share/applications/firefox-esr.desktop ~/Desktop/
                                                                             
┌──(kali㉿kali)-[~]
└─$ chmod +x ~/Desktop/firefox-esr.desktop
                                                                             
┌──(kali㉿kali)-[~]
└─$ ls -l ~/.local/share/applications/ | grep -i worm
                                                                             
┌──(kali㉿kali)-[~]
└─$ ls -l /usr/share/applications/ | grep -i worm
                                                                             
┌──(kali㉿kali)-[~]
└─$ didn't bring back anything, so we went to option <next> inorder to create a dedicated browser for wormgpt
quote> cat <<EOF > ~/Desktop/wormgpt.desktop 
[Desktop Entry]
Version=1.0
Type=Application
Name=WormGPT
Comment=Open WormGPT Web Interface
Exec=firefox-esr https://wormgpt.ai
Icon=web-browser
Terminal=false
Categories=Network;
EOF

chmod +x ~/Desktop/wormgpt.desktop    
quote> that is the next one                    
quote> 
                                                                             
┌──(kali㉿kali)-[~]
└─$ cat <<EOF > ~/Desktop/wormgpt.desktop
[Desktop Entry]
Version=1.0
Type=Application
Name=WormGPT
Comment=Open WormGPT Web Interface
Exec=firefox-esr https://wormgpt.ai
Icon=web-browser
Terminal=false
Categories=Network;
EOF

chmod +x ~/Desktop/wormgpt.desktop
                                                                             
┌──(kali㉿kali)-[~]
└─$ in order to run it locally changes are made to the browser
in: command not found
                                                                             
┌──(kali㉿kali)-[~]
└─$ cat << 'EOF' > ~/.wormgpt_start.sh
#!/bin/bash
# 1. Navigate to your local WormGPT directory (Adjust this path if needed)
# cd ~/path/to/your/wormgpt/folder

# 2. Start your local server in the background (Uncomment your method)
# python3 app.py & 
# docker-compose up -d &

# 3. Wait a moment for the local server to spin up
sleep 2

# 4. Open the local web interface in Firefox
firefox-esr http://127.0.0.1:5000
EOF

chmod +x ~/.wormgpt_start.sh
                                                                             
┌──(kali㉿kali)-[~]
└─$ cd ~/path/to/your/wormgpt/folder                          
cd: no such file or directory: /home/kali/path/to/your/wormgpt/folder
                                                                             
┌──(kali㉿kali)-[~]
└─$ find ~ -type d -iname "*worm*" 2>/dev/null
/home/kali/.mozilla/firefox/blesnlen.default-esr/storage/default/https+++challenges.cloudflare.com^partitionKey=%28https%2Cwormgpt.net%29
/home/kali/.mozilla/firefox/blesnlen.default-esr/storage/default/https+++www.wormgpt.ai
/home/kali/.mozilla/firefox/blesnlen.default-esr/storage/default/https+++wormgpt.ai
/home/kali/WormGPT-V2.0
┌──(kali㉿kali)-[~]
└─$ ls -l ~/WormGPT-V2.0
total 12
drwxrwxr-x 4 kali kali 4096 Jun 16 06:00 mainAI
-rw-rw-r-- 1 kali kali 5756 Jun 16 05:04 README.md
┌──(kali㉿kali)-[~]
└─$ ls -l ~/WormGPT-V2.0/mainAI
total 28
-rw-rw-r-- 1 kali kali 2312 Jun 16 05:04 ai_client.py
-rw-rw-r-- 1 kali kali  239 Jun 16 06:00 config.json
-rw-rw-r-- 1 kali kali 6615 Jun 16 05:04 main.py
drwxrwxr-x 2 kali kali 4096 Jun 16 05:17 __pycache__
-rw-rw-r-- 1 kali kali    9 Jun 16 05:04 requirements.txt
drwxrwxr-x 2 kali kali 4096 Jun 16 05:04 system-prompts 
┌──(kali㉿kali)-[~]
└─$ cat << 'EOF' > ~/.wormgpt_start.sh
#!/bin/bash
# 1. Navigate to the core execution directory
cd ~/WormGPT-V2.0/mainAI

# 2. Spin up the local local instance using Python
python3 main.py &

# 3. Give the local server 3 seconds to bind to its port
sleep 3

# 4. Fire up Firefox to the local server
# Note: If it runs on a port other than 5000 (like 8000 or 8080), change it here.
firefox-esr http://127.0.0.1:5000
EOF

chmod +x ~/.wormgpt_start.sh
┌──(kali㉿kali)-[~]
└─$ cat << 'EOF' > ~/.wormgpt_start.sh

heredoc> python3 main.py &

heredoc> sleep 3

heredoc> firefox-esr http://127.0.0.1:5000

heredoc> EOF                                      
┌──(kali㉿kali)-[~]
└─$ chmod +x ~/.wormgpt_start.sh             
┌──(kali㉿kali)-[~]
└─$ cat << 'EOF' > ~/.wormgpt_start.sh

python main.py & 

sleep 3

firefox-esr http://127.0.0.1:5000

EOF
┌──(kali㉿kali)-[~]
└─$ chmod +x ~/.wormgpt_start.sh      
┌──(kali㉿kali)-[~]
└─$ cat <<EOF > ~/Desktop/wormgpt.desktop
[Desktop Entry]
Version=1.0
Type=Application
Name=WormGPT (Local)
Comment=Launch Local WormGPT CLI
Exec=bash -c "$HOME/.wormgpt_start.sh; exec bash"
Icon=honeypot
Terminal=true
Categories=Network;Utility;
EOF

chmod +x ~/Desktop/wormgpt.desktop             
┌──(kali㉿kali)-[~]
└─$ cat << 'EOF' > ~/.wormgpt_start.sh   

python3 main.py &

sleep 3

firefox-esr http://127.0.0.1:5000

EOF
┌──(kali㉿kali)-[~]
└─$ chmod +x ~/.wormgpt_start.sh      
┌──(kali㉿kali)-[~]
└─$ cat <<EOF > ~/Desktop/wormgpt.desktop
[Desktop Entry]
Version=1.0      
Type=Application
Name=WormGPT (Local)
Comment=Launch Local WormGPT CLI
Exec=bash -c "$HOME/.wormgpt_start.sh; exec bash"
Icon=honeypot
Terminal=true
Categories=Network;Utility;
EOF

chmod +x ~/Desktop/wormgpt.desktop             
┌──(kali㉿kali)-[~]
└─$ 



$ pwsh
/usr/share/kali-menu/exec-in-shell: 1: eval: pwsh: not found
┌──(kali㉿kali)-[~]
└─$ find ~ -type d -iname "*evilgpt*" 2>/dev/null
                                                                             
┌──(kali㉿kali)-[~]
└─$ find / -type d -name "*evil*" 2>/dev/null | grep -vE "(sys|proc|dev|lib|share|mozilla|chromium)"
                                                                             
┌──(kali㉿kali)-[~]
└─$ cat <<EOF > ~/Desktop/evilginx.desktop
[Desktop Entry]
Version=1.0
Type=Application
Name=Evilginx2 (Local)
Comment=Launch Local Evilginx Framework
Exec=pkexec evilginx2
Icon=kali-ghost
Terminal=true
Categories=Network;Utility;
EOF

chmod +x ~/Desktop/evilginx.desktop
                                                                             
┌──(kali㉿kali)-[~]
└─$ find ~ -type f \( -name "*msty*" -o -name "*Msty*" \) 2>/dev/null
/home/kali/Downloads/MstyStudio_amd64.deb
/home/kali/.local/share/Trash/files/MstyStudio_x86_64.AppImage
/home/kali/.local/share/Trash/files/MstyStudio_amd64(1).deb
/home/kali/.local/share/Trash/info/MstyStudio_amd64(1).deb.trashinfo
/home/kali/.local/share/Trash/info/MstyStudio_x86_64.AppImage.trashinfo
                                                                             
┌──(kali㉿kali)-[~]
└─$ since It looks like you have the installer sitting right there in your Downloads folder: /home/kali/Downloads/MstyStudio_amd64.deb (and the AppImage versions were sent to the Trash).

Since it's a .deb package, the best move is to actually install it system-wide first. Once installed, it will automatically register itself, create its own official desktop icon, and add itself to your Kali application menu without us needing to build a launcher manually.
quote> we reinstall p[ackage
quote> launch or copy to desktop  
quote> 
                                                                             
┌──(kali㉿kali)-[~]
└─$ sudo apt install ~/Downloads/MstyStudio_amd64.deb
[sudo] password for kali: 
Sorry, try again.
[sudo] password for kali: 
Note, selecting 'mstystudio' instead of '/home/kali/Downloads/MstyStudio_amd64.deb'
mstystudio is already the newest version (2.8.2).
The following packages were automatically installed and are no longer required:
  enchant-2                 libmbedcrypto16  libsox-fmt-base
  libabsl20240722           libmbedtls21     libsvtav1enc2
  libavc1394-0              libmbedx509-7    libteamdctl0
  libbabeltrace1            libnsl2          libunibreak6
  libboost-iostreams1.83.0  libpoppler147    libwoff1
  libboost-thread1.83.0     libpostal-data   libxmlsec1-1
  libgdal38                 libpostal1       libxmlsec1-openssl1
  libicu76                  libraw23t64      libzxing3
  libio-pty-perl            libsdl2-classic  postgresql-common-dev
  libipc-run-perl           libsimdutf31     python3-typeshed
  libllhttp9.3              libsodium23      python3-tz
Use 'sudo apt autoremove' to remove them.

Summary:
  Upgrading: 0, Installing: 0, Removing: 0, Not Upgrading: 31
                                                                             
┌──(kali㉿kali)-[~]
└─$ cp /usr/share/applications/msty*.desktop ~/Desktop/ 2>/dev/null || cp /usr/share/applications/*msty*.desktop ~/Desktop/
cp: cannot stat '/usr/share/applications/*msty*.desktop': No such file or directory
                                                                             
┌──(kali㉿kali)-[~]
└─$ ls -l /usr/share/applications/ | grep -i msty
-rw-r--r-- 1 root root   221 Jun 15 01:34 MstyStudio.desktop
                                                                             
┌──(kali㉿kali)-[~]
└─$ cp /usr/share/applications/MstyStudio.desktop ~/Desktop/
                                                                             
┌──(kali㉿kali)-[~]
└─$ chmod +x ~/Desktop/MstyStudio.desktop 
                                                                             
┌──(kali㉿kali)-[~]
└─$ ls -l /usr/share/applications/ | grep -i mousepad
-rw-r--r-- 1 root root  9880 Mar  7 08:36 org.xfce.mousepad.desktop
-rw-r--r-- 1 root root  8057 Mar  7 08:36 org.xfce.mousepad-settings.desktop
                                                                             
┌──(kali㉿kali)-[~]
└─$ cp /usr/share/applications/org.xfce.mousepad.desktop ~/Desktop/ 2>/dev/null || cp /usr/share/applications/mousepad.desktop ~/Desktop/
                                                                             
┌──(kali㉿kali)-[~]
└─$ chmod +x ~/Desktop/*mousepad*.desktop
                                                                             
┌──(kali㉿kali)-[~]
└─$ 
