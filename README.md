# Ansible Control Node Instance in AWS Playbook

Deploy an AWS EC2 instance of a Linux VM with Ansible.  You may complete everything below within the [AWS Free Tier](https://aws.amazon.com/free).  If you have never deployed an AWS EC2 instance, you should first read [Deploy an EC2 Instance from the AWS Console](https://github.com/1homas/Ansible_AWS_EC2_Instance/blob/main/Deploy_EC2_Instance_from_AWS_Console.md) to understand the process and the virtual private cloud (VPC) components involved.


## Quick Start

1. Clone this repository:  

    ```bash
    git clone https://github.com/1homas/Ansible_Control_Node_AWS
    ```

1. Create your Python environment and install Ansible:  

    ```bash
    pipenv install
    pipenv install -r requirements
    pipenv shell
    ```

    If you have any problems installing Python or Ansible, see [Installing Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html).

1. Export your AWS Access & Secret keys into your terminal environment:  

    ```bash
    export AWS_REGION='us-west-1'
    export AWS_ACCESS_KEY='AKIAIOSF/EXAMPLE+KEY'
    export AWS_SECRET_KEY='wJalrXUtnFEMI/K7MDENG/bPxRfi/EXAMPLE+KEY'
    ```

    or you may source these variables from a file:

    ```bash
    source ~/.secrets/aws.sh
    ```

1. Run the Ansible playbook:  

    ```bash
    ansible-playbook main.yaml
    ```

1. SSH to your new running instance:  

    > ⚠ Replace the `{hostname}` with the dynamically assigned public IP address!

    ```bash
    ssh -i ~/.ssh/ansible_control_node.pem ubuntu@{hostname}
    ```

1. Run commands:

    ```bash
    ansible -m shell -a "ls" all
    ansible -m shell -a "ansible --version" all
    ansible -m shell -a "apt list --upgradable" all
    ```

1. When you are done, terminate the instances and delete all resources to prevent surprise AWS bills:

    ```bash
    ansible-playbook terminate.yaml
    ```




## License

This repository is licensed under the [MIT License](https://choosealicense.com/licenses/mit/).




