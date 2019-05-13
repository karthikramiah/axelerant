Pre-requisites:
----------------

1. 2 or more Ubuntu machines/VM's
2. Install Ansible in one of machines
3. Generate SSH key on the Ansible workstation and copy it to the authrized_keys of the other machines for Ubuntu user.
4. Modify the /etc/ansible/hosts file with the list of ip addresses of the other machines under the name of "dev" hostgroup.

		[dev]
                3.86.31.25


Procedure:
----------

1. Clone the git on the ansoble workstation.
2. To provide an user with SSH access

    a. Generate a SSH key for that user
    b. Store the key in a particular location in the ansible workstation
    c. Execute the below command in the ansible workstation.

     ansible-playbook -i /etc/ansible/hosts ssh_add_user.yml -e "user_name=john key_path=/home/ubuntu/.ssh/id_rsa.pub"

     Where "john" is the username to be provided with the SSH access
           "key_path" is the location in the ansible workstation where you have stored the Public key of that user

3. To revoke ssh access to a particular user run the below command in the ansible workstation

	ansible-playbook -i /etc/ansible/hosts ssh_revoke_user.yml -e "user_name=john"
   
         Where "john" is the username
