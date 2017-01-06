F5 OpenStack Ansible
====================

|slack badge|

This repository houses ansible playbooks, modules, and roles for deploying/configuring F5 OpenStack components.

Prerequisites
-------------

To use these playbooks, install ansible:

.. code:: shell

    $ pip install ansible

Directory Layout
----------------

The current directory structure is as follows:

.. code::

    playbooks/
        playbookX.yaml      # A playbook acts a specification for the tasks and roles you wish to deploy
        roles/              # Roles group snippets of associated tasks
            roleX/          # A specific role, such as 'configure_lbaasv2_agent'
                tasks/      # Tasks associated with a specific role
                vars/       # Variables related to a specific role
            roleY/          # Another role, such as 'pip install_lbaasv2_driver'
        vars/               # Global variables for a single playbook, separted into specific files

Usage
-----

In general, to use the playbooks within, one would define a hosts file. As of now, a sample `hosts` file exists, but this is just an example. For more information on the allowed inventory (hosts) parameters, see the `Ansible Inventory Doc <http://docs.ansible.com/ansible/intro_inventory.html#list-of-behavioral-inventory-parameters>`_.

Once you've setup your host file with the appropriate parameters, you may need to configure a YAML variables file with the appropriate key values related to your playbook. These are found in the `playbooks/vars` directory. If no YAML file exists for a particular playbook, please add one with the same name as the playbook appended with *_vars.yaml*. From there, you can run your ansible playbook:

.. code:: shell

    $ ansible-playbook -i <my_hosts_file> <my_playbook>

Copyright
---------

Copyright 2016-2017 F5 Networks Inc.

License
-------

Apache V2.0
~~~~~~~~~~~

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.  See the License for the specific language governing permissions and limitations under the License.

Contributor License Agreement
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Individuals or business entities who contribute to this project must have completed and submitted the `F5 Contributor License Agreement <http://f5-openstack-docs.readthedocs.org/en/latest/cla_landing.html>`_ to Openstack_CLA@f5.com prior to their code submission being included in this project.

.. |slack badge| image:: https://f5-openstack-slack.herokuapp.com/badge.svg
    :target: https://f5-openstack-slack.herokuapp.com/
    :alt: Slack
