# ansiblesimpleautomation








# Add the Ansible repository to your package manager.
sudo add-apt-repository --yes --update ppa:ansible/ansible

# Update the list of available packages.
sudo apt update

# Install Ansible.
sudo apt install ansible

# Test connectivity to all hosts.
ansible all -m ping

# Create a directory named "vprofile."
mkdir vprofile

# Change into the "vprofile" directory.
cd vprofile/

# Create a subdirectory named "exercise1."
mkdir exercise1

# Change into the "exercise1" directory.
cd exercise1/

# Edit the "inventory" file to list managed hosts.
vi inventory

# Edit the SSH private key file (typically named "webkey.pem").
vim webkey.pem

# Check connectivity to the "web01" host using the updated configuration.
ansible web01 -m ping -i inventory

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
