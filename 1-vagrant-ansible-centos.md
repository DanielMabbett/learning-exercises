Prerequisites:

Vagrant
VirtualBox
Ansible
Steps:

Create a new directory for your project.
Inside the directory, create a file called Vagrantfile.
In the Vagrantfile, add the following code:
```Code snippet
Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.network "private_network", ip: "192.168.1.100"
  config.vm.network "private_network", ip: "192.168.1.101"
  config.vm.network "private_network", ip: "192.168.1.102"
end
```
Save the Vagrantfile file.
From the command line, navigate to the directory where you created the Vagrantfile file.
Run the following command to create the VMs:
```
vagrant up
```
Once the VMs are created, you can connect to them using SSH. The default username and password for CentOS is vagrant and vagrant.

Once you are connected to a VM, you can install nginx using the following command:

```Code snippet
sudo yum install nginx
Use code with caution. Learn more
To verify that nginx is installed, you can run the following command:
Code snippet
sudo service nginx status
```
Ansible Playbook:

You can also use Ansible to install nginx on the VMs. To do this, create a file called playbook.yml and add the following code:

```Code snippet
---
- hosts: all
  become: yes
  tasks:
    - name: Install nginx
      apt:
        name: nginx
        state: present
```
Save the playbook.yml file.

To run the playbook, from the command line, navigate to the directory where you created the playbook.yml file and run the following command:

```
ansible-playbook playbook.yml
```
The playbook will install nginx on all of the VMs.

Testing:

Once nginx is installed, you can test it by opening a web browser and navigating to the IP address of one of the VMs. You should see the nginx welcome page.

Conclusion:

This exercise has shown you how to create a vagrant of 3 VMs using a CentOS image, and then use Ansible to target these containers and install nginx on the 3 images.
