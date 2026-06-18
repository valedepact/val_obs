source = https://github.com/adityatelange/evil-winrm-py

### how
Prepare your Environment (Linux)

#Update your package list and install dependencies
sudo apt update
sudo apt install gcc python3-dev libkrb5-dev krb5-pkinit

#Create a virtual environment to keep your system Python clean
python3 -m venv evil-winrm-env
source evil-winrm-env/bin/activate

Install the Package
 #Standard installation
pip install evil-winrm-py

#If you specifically need Kerberos authentication support
pip install evil-winrm-py[kerberos]