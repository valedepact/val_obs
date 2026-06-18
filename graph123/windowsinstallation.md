$ pwsh
/usr/share/kali-menu/exec-in-shell: 1: eval: pwsh: not found
┌──(kali㉿kali)-[~]
└─$ cd "/home/kali/VirtualBox VMs/win10VM/"
                                                                             
┌──(kali㉿kali)-[~/VirtualBox VMs/win10VM]
└─$ ls   
win10VM.vbox  win10VM.vbox-prev  win10VM.vdi
                                                                             
┌──(kali㉿kali)-[~/VirtualBox VMs/win10VM]
└─$ rm win10VM.vbox        
                                                                             
┌──(kali㉿kali)-[~/VirtualBox VMs/win10VM]
└─$ cp win10VM.vbox-prev win10VM.vbox      
                                                                             
┌──(kali㉿kali)-[~/VirtualBox VMs/win10VM]
└─$ ls
win10VM.vbox  win10VM.vbox-prev  win10VM.vdi
                                                                             
┌──(kali㉿kali)-[~/VirtualBox VMs/win10VM]
└─$ VBoxManage startvm win10VM
Waiting for VM "win10VM" to power on...
VM "win10VM" has been successfully started.
                                                                             
┌──(kali㉿kali)-[~/VirtualBox VMs/win10VM]
└─$ cd "/home/kali/VirtualBox VMs/win10VM/"
cd: no such file or directory: /home/kali/VirtualBox VMs/win10VM/
                                                                             
┌──(kali㉿kali)-[~/VirtualBox VMs/win10VM]
└─$ ls                                     
                                                                             
┌──(kali㉿kali)-[~/VirtualBox VMs/win10VM]
└─$ cd ..                                  
                                                                             
┌──(kali㉿kali)-[~/VirtualBox VMs]
└─$ ..                    
                                                                             
┌──(kali㉿kali)-[~]
└─$ ls
 2026-06-15-12-58-30.030-VirtualBoxVM-27785.log     live.txt
 2026-06-15-13-06-47.007-VirtualBoxVM-83580.log     Music
 2026-06-15-13-52-13.095-VirtualBoxVM-100955.log    openvpn-ca
 2026-06-16-08-01-30.090-VirtualBoxVM-111616.log    Pictures
 2026-06-16-10-21-25.028-VirtualBoxVM-3226517.log   Projects
 2026-06-16-10-38-08.069-VirtualBoxVM-3232158.log   Public
 2026-06-16-10-55-58.033-VirtualBoxVM-3249997.log   quick_scan.gnmap
 2026-06-16-11-36-28.075-VirtualBoxVM-3275226.log   quick_scan.nmap
 Applications                                       quick_scan.xml
 client1.ovpn                                       Templates
 Desktop                                            Videos
 Documents                                         'VirtualBox VMs'
 Downloads                                          vuln_scan.gnmap
 full_scan.gnmap                                    vuln_scan.nmap
 full_scan.nmap                                     vuln_scan.xml
 full_scan.xml                                      WormGPT-V2.0
 KaliGPT
                                                                             
┌──(kali㉿kali)-[~]
└─$ cd "/home/kali/VirtualBox VMs/win10VM/"
cd: no such file or directory: /home/kali/VirtualBox VMs/win10VM/
                                                                             
┌──(kali㉿kali)-[~]
└─$ VBoxManage startvm win10VM             
VBoxManage: error: Could not find a registered machine named 'win10VM'
VBoxManage: error: Details: code VBOX_E_OBJECT_NOT_FOUND (0x80bb0001), component VirtualBoxWrap, interface IVirtualBox, callee nsISupports
VBoxManage: error: Context: "FindMachine(Bstr(pszVM).raw(), machine.asOutParam())" at line 907 of file VBoxManageMisc.cpp
                                                                             
┌──(kali㉿kali)-[~]
└─$ VBoxManage showvminfo win10VM | grep -iE "\.iso|dvd|empty"
VBoxManage: error: Could not find a registered machine named 'win10VM'
VBoxManage: error: Details: code VBOX_E_OBJECT_NOT_FOUND (0x80bb0001), component VirtualBoxWrap, interface IVirtualBox, callee nsISupports
VBoxManage: error: Context: "FindMachine(Bstr(VMNameOrUuid).raw(), machine.asOutParam())" at line 3248 of file VBoxManageInfo.cpp
                                                                             
┌──(kali㉿kali)-[~]
└─$ VBoxManage list vms
"kaliVm" {c93fa8ae-9b47-45ce-b86d-cb55805c0235}
"win10vm" {9ad1bf35-99d7-49af-8183-ed797ffe73e5}
                                                                             
┌──(kali㉿kali)-[~]
└─$ VBoxManage showvminfo win10vm | grep -iE "\.iso|dvd|empty"
Boot Device 2:               DVD
    Location: "/home/kali/Documents/Windows.iso"
                                                                             
┌──(kali㉿kali)-[~]
└─$ 


-------
┌──(kali㉿kali)-[~]
└─$ ls -lh /home/kali/Documents/Windows.iso
-rwxr-xr-x 1 kali kali 4.6G Jun 16 05:14 /home/kali/Documents/Windows.iso
                                                                             
┌──(kali㉿kali)-[~]
└─$ sha256sum /home/kali/Documents/Windows.iso
476262380ab54c0d756bbda2d3af1dae731698c47247ec086f8b4a74c55a8881  /home/kali/Documents/Windows.iso           
┌──(kali㉿kali)-[~]
└─$ 

