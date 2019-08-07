# Description

This Ansible playbook does following steps at one go:

1. Create EC2 and register details of the created instance as variable `result_ec2` for using in later steps.
2. Add EC2 instance to playbook's in-memory inventory.
3. Wait until SSH access to the EC2 instance becomes available.
4. Apply Mary's role `ql_common_linux`.
5. Create AMI image from the configured EC2 instance.
6. Terminate EC2.

The reason of such approach was Mary's mentioning of cost-related concerns. Implemented solution runs EC2 instance for the minimal time, produces the result AMI and terminates the EC2.

# Assumptions

 1. Mary's email didn't specify what AMI to base from for her EC2. So I put EC2 parameters into `group_vars/all/vars.yml` so that she can change them conviniently.

 2. This EC2 instance is created in a default Security Group and you can change that via `group_vars/all/vars.yml`. However you need to **make sure that your SG allows incoming tcp connections on 22 port**.

# Before you run this playbook

## Create a vault with your AWS credentials

```bash
ansible-vault create group_vars/all/vault.yml
```

And add your aws credentials like below:
```yaml
aws_access_key: "XXXXXXXXXXXX"
aws_secret_key: "YYYYYYYYYYYYYYYYYY"
```

## Create key-pair in AWS EC2 console

And then:
 - Save private key in this repo as filename `.ssh/test01.pem`
 - Set proper permissions of this file:
 ```bash
 chmod 0600 .ssh/test01.pem
 ```

# Running the playbook

```bash
ansible-playbook --vault-id @prompt -v create_ami.yml -vv
```

## Configure AWS Subnet id 

# Potential problems and how to troubleshoot

1. This playbook does not create any inventory file locally.
2. If the playbook fails then you can't run specific steps of the playbook individually.
3. If the playbook fails you are responsible for manually cleaning up any half-configured EC2 instances.
4. For troubleshooting you can ssh into the created EC2 using command:
```bash
ssh -i .ssh/test01.pem ec2-user@INSTANCE_IP
```