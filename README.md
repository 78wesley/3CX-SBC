## Requirements
- A server running 3CX server
- Linux subsystem or a Linux system with Ansible installed (Installation instructions below, Stap 1)
- A Raspberry Pi flashed with [Raspberry Pi OS](https://www.raspberrypi.org/downloads/raspberry-pi-os/) to install the SBC on (Raspberry Pi OS Lite recommended).
- SSH enabled on your Raspberry PI, instructions can be found [here](https://www.raspberrypi.org/documentation/remote-access/ssh/README.md) (On the side Step 3 recommended).

## 1. Install Ansible & other dependencies
```sh
apt install ansible && apt install sshpass -y
```
```sh
mkdir 3CXSBC && cd 3CXSBC
```
## 2. Download the Ansible script and the hosts file.
```sh
wget https://raw.githubusercontent.com/78wesley/3CX-SBC/main/hosts && wget https://raw.githubusercontent.com/78wesley/3CX-SBC/main/3cxsbc.yml
```
## 3. Configure hosts
Go to the hosts file and replace <ip> under **[all]** to the IP/Hostname of your Raspberry Pi on which you would like to install the 3CX SBC.  
```sh
nano hosts
```
## 4. Run the Ansible script
When you run the ansible script, the script will asks you to fill in the following information:
- What is the Web Url of 3CX?
- What is the SBC Authentication KEY ID?
- What will be the new password of the Raspberry Pi?
  
You can find this information if you add a new 3CX SBC within 3CX found at **SIP-Trunk** > **Add SBC**. 

I recommend to use the SBC Password as the Raspberry Pi password so you will always be able to retrieve the password.
```sh
ansible-playbook -i hosts 3cxsbc.yml
```
## Install the SBC without ansible (default SBC installer with headless install functionality)
Replace URL and KEY for your own SBC url and key.
```sh
wget -O- https://raw.githubusercontent.com/78wesley/3CX-SBC/main/3cxsbc.sh | bash /dev/stdin -u "URL" -k "KEY" -a 1
```
