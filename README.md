# ansiblesimpleautomation








# Add the Ansible repository to your package manager.
sudo add-apt-repository --yes --update ppa:ansible/ansible

# Update the list of available packages.
sudo apt update

# Install Ansible.
sudo apt install ansible

# Test connectivity to all hosts.
ansible all -m ping

# Create a directory named "myprfoile"
mkdir myprofile

# Change into the "vprofile" directory.
cd myprofile/

# Create a subdirectory named "exercise1."
mkdir exercise1

# Change into the "exercise1" directory.
cd exercise1/

# Edit the "inventory" file to list managed hosts.
vi inventory

# Edit the SSH private key file (typically named "webkey.pem").
vim webkey.pem
keep the pem key in exec folder itself

# Check connectivity to the "web01" host using the updated configuration.
ansible web01 -m ping -i inventory
chmod 400 webkey.pem


# Display the contents of the Ansible configuration file.
sudo cat /etc/ansible/ansible.cfg

# Rename the original Ansible configuration file to create a backup.
mv /etc/ansible/ansible.cfg /etc/ansible/ansible.cfg_backup

# Generate a new Ansible configuration file with default settings.
ansible-config init --disabled -t all > /etc/ansible/ansible.cfg

# Edit the new Ansible configuration file.
vim /etc/ansible/ansible.cfg
#change hostkey_chnage_ to yes
# Re-test connectivity to the "web01" host after adjusting file permissions.
ansible web01 -m ping -i inventory

# Set strict file permissions on the SSH private key.
chmod 400 webkey.pem

# Re-test connectivity to the "web01" host with the updated key permissions.
ansible web01 -m ping -i inventory
 #ansible dbservers -m ping -i inventory
 ansible webservers -m ping -i inventory
 ansible dc_oregon -m ping -i inventory
 ansible all -m ping -i inventory
 ansible 'web*' -m ping -i inventory




 # Ansible Project README

This README provides essential Ansible commands for managing your hosts and configuring services. Make sure to replace placeholders with actual values specific to your environment.

## Basic Ansible Commands


# Test Host Connectivity:
ansible all -m ping -i inventory

# Installing the Apache HTTP Server (`httpd`):

# On a Specific Host (e.g., "web01"):
ansible web01 -m ansible.builtin.yum -a "name=httpd state=present" -i inventory

# On a Specific Host with Privilege Escalation:
ansible web01 -m ansible.builtin.yum -a "name=httpd state=present" -i inventoryhttps://github.com/mohammedsalmanj/ansiblesimpleautomation/tree/main --become

# On a Group of Hosts (e.g., "webservers") with Privilege Escalation:
ansible webservers -m ansible.builtin.yum -a "name=httpd state=present" -i inventory --become

# Enabling the Apache HTTP Server (`httpd`):

# On a Specific Host with Privilege Escalation:
ansible web01 -m ansible.builtin.service -a "name=httpd state=started enabled=yes" -i inventory --become

# On a Group of Hosts (e.g., "webservers") with Privilege Escalation:
ansible webservers -m ansible.builtin.service -a "name=httpd state=started enabled=yes" -i inventory --become

# Copying a File to Remote Hosts (e.g., "index.html"):

# On a Group of Hosts (e.g., "webservers") with Privilege Escalation:
ansible webservers -m ansible.builtin.copy -a "src=local-index.html dest=/var/www/html/index.html" -i inventory --become

# Changing Security Group Rules to Allow HTTP (Port 80) Traffic:

# Command to Be Added Based on Your Specific Cloud Provider.
#step to execute playbook
#ansible-playbook -i inventory web-db.yaml


#changed sg of webserver from anywhere http 80



#Ansible Playbook Execution Commands

#These commands are used to work with Ansible playbooks. Replace `web-db.yaml` with the actual name of your playbook.

#ansible-playbook -i inventory web-db.yaml

#RUN 
#ansible-playbook -i inventory web-db.yaml -v
#ansible-playbook -i inventory web-db.yaml --syntax-check
#ansible-playbook -i inventory web-db.yaml -C


#####
#ansible -i inventory -m setup web01


