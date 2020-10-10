## Requirements
- Linux subsystem or a Linux system in the network
- Ansible(Install below)
- 3CX Server

## 1. Install Ansible
```sh
apt-add-repository  ppa:ansible/ansible && apt install ansible
```
```sh
cp -R /etc/ansible/ myansible
```
```sh
cd myansible
```
## 2. Download the hosts and ansible config files
```sh
wget https://raw.githubusercontent.com/78wesley/3CX-SBC/main/3cxsbc.yml && wget https://raw.githubusercontent.com/78wesley/3CX-SBC/main/hosts
```
## 3. Change hosts IP
Go to the hosts file and change the hostname under **[all]** to the IP of your system.
```sh
nano hosts
```
## 4. Run the bash script
In the bash script you will be ask for the following things.
- What will be the password of the system?
- What is the Web Url?
- What is the Authentication KEY ID?

You can find this information if you add a new 3CX SBC at **SIP-Trunk > Add SBC**. 

I recommend to use the SBC Password as the System password.
```sh
ansible-playbook -i hosts 3cxsbc.sh
```
## How to use it manualy?
Replace URL and KEY for your own SBC url and key.
```sh
wget -O- https://raw.githubusercontent.com/78wesley/3CX-SBC/main/3cxsbc.sh | bash /dev/stdin -u "URL" -k "KEY" -a 1
```
