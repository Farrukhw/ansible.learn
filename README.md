# Ansible learning
## This repository contains the files which are being created while learning Ansible. 

MyInventory.txt: The custom ansible inventory
MyPlaybook.yml: The ansible playbook
Dockerfile: This is used to build a customized Ubuntu image with ssl service enabled and some necessary tools installed.
  *Warning:* id_rsa.pub is not included in this repository, so your Docker build might fail without it.
  *Note:*  This is a public ssl key, and the user have to generate it from their own host machines. 
docker-compose: Using the image produced by Dockerfile, i.e. farrukhw/ubntu.latest.
