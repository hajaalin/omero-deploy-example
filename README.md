# omero-deploy-example

This example uses http://hakunin.com/six-ansible-practices, points 1.2, 1.3 and 1.4. It assumes that you have private/public key pair ~/.ssh/id_rsa(.pub).

Clone this repository (or your fork).
```
git clone https://github.com/hajaalin/omero-deploy-example.git
cd omero-deploy-example
```  

```
# Start dev VM.
vagrant up

# Get versioned roles (for example to use a more detailed role PostgreSQL).
ansible-galaxy install -f -r requirements.yml -p ./roles

# Install on dev VM.
ansible-playbook -i inventory/dev53 site.yml

# Install on test server. Use Ansible Vault to protect secrets.
# ansible-playbook --vault-password-file=~/.ansible_vault_passes/omero-deploy -i inventory/test site.yml --become --ask-become-pass

```
