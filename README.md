# Readme (jenkins-ckan-docker) EKO
**Setup Jenkins**
```
ansible-playbook jenkins_setup.yml -e "target=jenkins.master"  -t install,setup
```

**Configure Jenkins**

Install and setup ansible on jenkins machine
```
sudo apt-get install curl wget python-dev git  -y
curl -O https://bootstrap.pypa.io/get-pip.py
sudo python get-pip.py
sudo apt-get update -y
sudo apt-get install libpq-dev python-dev libxml2-dev libxslt1-dev libldap2-dev libsasl2-dev libffi-dev python-dev build-essential git wget PyYAML jinja2 paramiko boto3 ansible -y -q
sudo pip install -U boto (it needs latest boto version or we get errors with ec2 modules)
```
##NOTE
Create ssh key for seamless ssh of jenkins user to deployment machine[preferable ansible user]

##TODO
This can also be automated as part of ansibl-ized process
``` 
- Setup of ansible 
- Configure Jenkins 
- Installing Plugins
- Creating Jenkins jobs
```
**Install Following Plugins on jenkins**
```
- SSH plugin
- Anisble 
```
**Jenkins job for CKAN deployment**
```
- Contains setup of git and other dependencies
- Clones CKAN git repo [if not installing from apt | package]
- Deploy CKAN prerequisites
- Deploy CKAN
```
E.g.
```
ansible-playbook ckan_deploy.yml -e "target=ckan.master"  -t install,setup
```