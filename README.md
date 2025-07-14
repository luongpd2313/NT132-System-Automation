
# 🔧 Automated DVWA Deployment using Ansible

## 📌 Overview
This project automates the deployment of [DVWA (Damn Vulnerable Web Application)](https://github.com/digininja/DVWA) using **Ansible**. It focuses on secure configuration, repeatability, and ease of deployment across multiple hosts. 

## 📂 Project Structure
- **Ansible Control Node**: `192.168.80.137`
- **Managed Nodes**:
  - `192.168.80.136` - DVWA host 1
  - `192.168.80.139` - DVWA host 2

## 🚀 Features
-  Automated installation of Apache, MySQL, PHP
-  Ansible-based setup using YAML playbooks
-  SSH key-based authentication setup
-  Inventory file for multi-host control
-  Configuration of DVWA with MySQL and Apache
-  Idempotent playbooks with error handling

## 🛠️ Setup Steps (Summary)
Before running this playbook you will need to run collection_install.sh first but you do need ansible installed before that.
```bash
chmod +x collection_install.sh
./collection_install.sh
```
# Install Ansible on Kali 
```bash
sudo apt update && sudo apt install ansible -y
```
# Install Ansible on Ubuntu
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install software-properties-common
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt install ansible
```
# Install Ansible with pip
Python3 is installed automatically in Ubuntu & Kali Linux, so we just need to install pip via:
```bash
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python3 get-pip.py --user
```
After that, we will install ansible via pip and verify if it's installed.
```bash
python3 -m pip install --user ansible
ansible --version
```
1. **Generate SSH key and copy to managed nodes**
2. **Create `inventory.ini` file**  
<img width="1034" height="89" alt="image" src="https://github.com/user-attachments/assets/8b91c63f-b70c-4405-a560-ffcbf6115efe" />

3. **Run Ansible playbooks** to:
   - Install dependencies
   - Deploy DVWA
   - Configure MySQL & Apache
```bash
ansible-playbook -i inventory.ini main.yml
```
4. **Verify deployment via browser** at `http://<host_ip>/setup.php`

## 📸 Demo Result
<img width="1284" height="363" alt="image" src="https://github.com/user-attachments/assets/d5063bea-1612-443e-b362-d5497472a367" />

Login credentials:
- Username: `admin`
- Password: `password`

## Conclusion
> “Ansible significantly reduced the manual overhead in setting up a secure DVWA environment, supporting future scalability and reproducibility.”

## Team Member Contributions

| Member                   | Responsibilities                                                                 | Contribution (%) |
|--------------------------|-----------------------------------------------------------------------------------|------------------|
| **Phung Duc Luong**      | Research, system installation, configuration, demonstration, presentation, slides | 100%             |
| **Ngo Minh Quan**        | Research, configuration, demonstration, presentation, slides                      | 100%             |
| **Chu Nguyen Hoang Phuong** | Research, system installation, configuration, demonstration, presentation          | 100%             |


## Appendix
- 📄 Final Report: `Group08_FinalReport.pdf`
- 🎯 Score Sheet: Present (4), Theory (4), Report (4), Demo (3)

## 📌 Note
> Managed nodes require **no agent**, only SSH access — aligning with Ansible’s agentless architecture.
