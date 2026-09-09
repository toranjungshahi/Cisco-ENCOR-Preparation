##### 1\. Install ansible and Cisco IOS collection on control node

* ###### Install

&#x09;**sudo apt-get install ansible**

&#x09;**ansible-galaxy collection install cisco.ios**



If using python venv, install ansible in the venv with below command

&#x09;**pip install ansible**

&#x09;

* ###### Verify installed collection

&#x09;**ansible-galaxy collection list**





##### 2\. Configure Cisco devices for SSH access

* ###### Set hostname and domain name (required for generating SSH key)

&#x09;**hostname** *host-name*

&#x09;**ip domain-name** *zukotek.com*



* ###### Generate RSA keys for SSH

&#x09;**crypto key generate rsa modulus 2048**

&#x09;

* ###### Configure local user for Ansible Automation with Priivilege 15

&#x09;**username** *cisco\_ansible* **privilege** **15** **secret** *c1sc0\_ans1ble*



* ###### Configure SSH version 2 and Vty lines

&#x09;**ip ssh version 2**

&#x09;**line vty 0 4**

&#x09;**transport input ssh**

&#x09;**login local**

&#x09;**exec-timeout** 0 0



##### 3\. Configure Inventory and Variables

* ###### Example inventory file inventory.ini

&#x09;\[Switches]

&#x09;192.168.1.3



&#x09;\[Routers]

&#x09;192.168.1.3



&#x09;\[Gateway]

&#x09;192.168.1.1



* ###### Method 1 to define variables, inline with ini file



\# --- Switches Section ---

\[Switches]

192.168.1.3



\[Switches:vars]

ansible\_user=cisco\_ansible  #privilege level 15

ansible\_password=c1sc0\_ans1ble

ansible\_connection=ansible.netcommon.network\_cli

ansible\_network\_os=cisco.ios.ios

ansible\_become= no



\# --- Routers Section (Assumed the router is running IOS-XR) ---

\[Routers]

192.168.1.3



\[Routers:vars]

ansible\_user=adminxr

ansible\_password=XRpassword123!

ansible\_connection=ansible.netcommon.network\_cli

ansible\_network\_os=cisco.iosxr.iosxr

\# Note: IOS-XR enters privilege 15 directly on login; become parameters are usually omitted.



\# --- Gateway Section (Assumed the gateway is running IOS-XR) ---

\[Gateway]

192.168.1.1



\[Gateway:vars]

ansible\_user=adminxr

ansible\_password=XRpassword123!

ansible\_connection=ansible.netcommon.network\_cli

ansible\_network\_os=cisco.iosxr.iosxr

\# Note: IOS-XR enters privilege 15 directly on login; become parameters are usually omitted.



* ###### Method 2 to define variables, Use group\_vars/ Directory



your-project-dir/

├── inventory.ini

├── site.yml (playbook)

└── group\_vars/

&#x20;   ├── Switches.yml

&#x20;   ├── Routers.yml

&#x20;   └── Gateway.yml





Create each .yml file inside group\_vars directory, for example Switches.yml as below:



\---

ansible\_user=admin

ansible\_password=Cisco123!

ansible\_connection=ansible.netcommon.network\_cli

ansible\_network\_os=cisco.ios.ios

ansible\_become=yes

ansible\_become\_method=enable

...



##### 4\. Create playbooks

###### Example: ConfigureInterface.yml



\---

\- name: Configure Interface #Human readable name of the playbook

&#x20; hosts: Switches #All hosts or host block from inventory file

&#x20; gather\_facts: no # Disable discovery. By default, Linux gathers facts about node using python. Cisco ios does not support python



&#x20; tasks: #List task to be performed

&#x20;   - name: Configure interface GigabitEthernet0/2 #Human readable name of the task

&#x20;     ios\_config: #Use this module from cisco.ios collection to configure interface. This module opens cli in global configuration mode

&#x20;       lines: #Actual commands in a list named lines

&#x20;         - description Configured by Ansible !!!

&#x20;         - ip address 10.10.12.1 255.255.255.0

&#x20;         - no shutdown

&#x20;       parents: interface GigabitEthernet0/2 #Object the ios\_config module is applied against.

...



##### 5\. Troubleshooting

* ###### If running from virtual env, ansible by default uses system python interpreter and can throw no package (paramiko) installed error.

&#x09;

&#x09;**Create a ansible.cfg file in project directory and include a line:** where venv is the virtual environment name.

&#x09;

&#x09;interpreter\_python = /home/toran/Ansible-lab/venv/bin/python3







&#x09;

