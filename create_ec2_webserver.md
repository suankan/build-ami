# Description

This Ansible playbook does following steps at one go:

1. Create EC2 based on Amazon Linux AMI and register details of the created instance as variable `result_ec2` for using in later steps.
2. Add EC2 instance to playbook's in-memory inventory.
3. Wait until SSH access to the EC2 instance becomes available.
4. Apply role `webserver`. Please refer to `webserver.md` to see what it does.

# Assumptions

1. This EC2 instance is created in a default Security Group and you can change that via `group_vars/all/vars.yml`. However you need to **make sure that your SG allows incoming tcp connections on 80 port**.

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
ansible-playbook --vault-id @prompt -v create_ec2_webserver.yml -vv
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