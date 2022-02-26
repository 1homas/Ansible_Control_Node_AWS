# Ansible AWS EC2 Instance Playbook

Deploy an AWS EC2 instance of a Linux VM.  You may complete everything below within the [AWS Free Tier](https://aws.amazon.com/free).  If you have never deployed an AWS EC2 instance, you should first read [Deploy an EC2 Instance from the AWS Console](Deploy_EC2_Instance_from_AWS_Console.md) to understand the process and the virtual private cloud (VPC) components involved.


## Quick Start

1. Clone this repository:  

    ```bash
    git clone https://github.com/1homas/_____repository_name_____
    ```

1. Create your Python environment and install Ansible:  

    ```bash
    pip install --upgrade pip
    pip install pipenv
    pipenv install --python 3.9
    pipenv install ansible boto boto3 botocore
    pipenv shell
    ```

    If you have any problems installing Python or Ansible, see [Installing Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html).

1. Export your AWS Access & Secret keys into your terminal environment:  

    ```bash
    export AWS_REGION='us-west-1'
    export AWS_ACCESS_KEY='AKIAIOSF/EXAMPLE+KEY'
    export AWS_SECRET_KEY='wJalrXUtnFEMI/K7MDENG/bPxRfi/EXAMPLE+KEY'
    ```

1. Run the Ansible playbook:  

    ```bash
    ansible-playbook main.yaml
    ```

1. SSH to your new running instance:  

    > ⚠ Replace the `{hostname}` with the dynamically assigned public IP address!

    ```bash
    ssh -i ./AWS_EC2_Instance_Test.private_key.pem ec2-user@{hostname}
    ```


1. Run commands:
    ```bash
    ansible -m shell -a "ansible --version" all
    ansible -m shell -a "apt list --upgradable" all
    ```
1. When you're done, you may terminate and remove the instances:

    ```bash
    ansible-playbook terminate.yaml
    ```




## License

This repository is licensed under the [MIT License](https://choosealicense.com/licenses/mit/).




