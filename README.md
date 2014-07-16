# Build Docker image by [Packer](http://www.packer.io/)

## How to run

Install Docker and Packer on the machine and execute the following command.

```
$ packer validate apache-base.json
$ packer build -var 'version=v1.0.0' -var 'base-image-version=v1.0.0' apache-base.json
```

Once packer creates a docker container, ansible is used to provision the container. Once container is provisioned an image is created and pushed to docker index.

## Ansible 

Ansible command that packer runs inside docker container

```
$ ansible-playbook {{.PlaybookFile}} -c local -i "127.0.0.1,"
```