# PECTOR DOCUMENTATION FOR PROJECT 12
Go to your Jenkins-Ansible server and create a new directory called ansible-config-artifact – we will store there all artifacts after each build.
`sudo mkdir /home/ubuntu/ansible-config-artifact`
Change permissions to this directory, so Jenkins could save files there `– chmod -R 0777 /home/ubuntu/ansible-config-artifact`
Go to Jenkins web console -> Manage Jenkins -> Manage Plugins -> on Available tab search for Copy Artifact and install this plugin without restarting Jenkins ![Jenkins](./images/Jenkins%20Configuration.png)
Create a new Freestyle project (you have done it in Project 9) and name it save_artifacts.
This project will be triggered by completion of your existing ansible project. Configure it accordingly: ![Jen set](./images/Jenkins%20setup.png)
update `site.yml` with `- import_playbook: ../static-assignments/common-del.yml` instead of `common.yml` and run it against dev server and change directory to `/home/ubuntu/ansible-config-artifact/` and run ansible all -m ping to confirm the availability of the host. ![playbook](./images/ansible-playbook%20command.png)
`ansible-playbook -i inventory/dev.yml playbooks/site.yml` ![Dependency](./images/Deleted%20wireshark.png)
CONFIGURE UAT WEBSERVERS WITH A ROLE ‘WEBSERVER’

Launch 2 fresh EC2 instances using RHEL 8 image, we will use them as our uat servers, so give them names accordingly – `Web1-UAT`and `Web2-UAT`.
To create a role, you must create a directory called roles/, relative to the playbook file or in `/etc/ansible/` directory
Create the directory/files structure manually. In the root folder, create a folder and name it webserverand inside webserver folder, create five more folders namely: README.md, defaults(create a file inside it and name it main.yml), handlers(inside handlers, create a file and name it main.yml), meta(jnside this folder, create a file and name it main.yml), tasks(inside tasks, create a file and name it main.yml). ![workspace](./images/Structure%20of%20the%20workspace.png)
![Tooling w1](./images/Tooling%20on%20w1.PNG)
![Tooling w2](./images/Tooling%20on%20w2.PNG)

THANKS