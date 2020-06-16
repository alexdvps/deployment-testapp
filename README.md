# **Test Application Deployment**

Project is dedicated to deploy a test application using Ansible.


### Ansible playbook and roles for provisioning and deploying test applications.

## Features

  * Provides tasks for provisioning and deploying a test application.
  * Provisions a server with all required applications and requirements.
  * Use git to checkout the application
  * Use Nginx as reverse proxy
  * Use Uwsgi to run the test application


### **Testing using Ansible playbooks**

### Run playbook
```bash
$ ansible-playbook -i 127.0.0.1 ansible/playbook.yml
```


### **Testing using Vagrant/Virtualbox**

Application Deployment on Vagrant/Virtualbox guest

### Run vagrant
```bash
$ vagrant up
```


### **Testing using Packer/AWS AMI**

This Packer configuration will generate Amazon Linux image.
Need to specify some aws related values in packer_vpc_vars.json

### Create-role
```bash
$ aws iam create-role --role-name packer --assume-role-policy-document '{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Principal": {"Service": "ec2.amazonaws.com"},
    "Action": "sts:AssumeRole",
    "Sid": ""
  }
}'
```

### Run packer
```bash
$ packer build --force -only=amazon-ebs -var-file=packer_vpc_vars.json packer_ubuntu_1604.json
```


### **Testing using Kubernetes**

Application Deployment on Kubernetes

### Run kubectl
```bash
$ kubectl apply -f kubernetes/deployment.yaml
```
