Deploying F5 OpenStack Agent and Driver with Ansible
====================================================

The playbook `agent_driver_deploy.yaml` will install the F5 OpenStack agent and driver with pip, debs, or rpms. To use the playbook:

1. Create or edit the given `hosts` file to add the IP address of your OpenStack controller. This is where the driver and agent will be installed. In here, also include the path to the private key file used to ssh into the OpenStack controller.

2. Edit the variables file referenced in the playbook at vars/agent_driver_deploy_vars.yaml. There are a few variables that have defaults from the Ansible roles. If you'd like to override any of these, uncomment them from the variables file and set your values accordingly. This installation allows for overcloud or undercloud deployment.

3. Run the playbook: ansible-playbook -i hosts agent_driver_deploy.yaml
