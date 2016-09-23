# omero-deploy-example

This example uses http://hakunin.com/six-ansible-practices, points 1.2, 1.3 and 1.4. It assumes that you have private/public key pair ~/.ssh/id_rsa(.pub).

Clone OME infrastructure and this repository (or your fork(s)).
```
git clone https://github.com/openmicroscopy/infrastructure.git
git clone
cd omero-deploy-example
```  

```
# Start dev VM.
vagrant up

# Get versioned roles (for example to use a more detailed role PostgreSQL).
./get_roles.sh

# Install on dev VM.
ansible-playbook -i inventory/dev ../infrastructure/ansible/training-server.yml

# Install on test server. Use Ansible Vault to protect secrets.
# ansible-playbook --vault-password-file=~/.ansible_vault_passes/omero-deploy -i inventory/test install.yml --become --ask-become-pass

```
