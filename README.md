# ansible-pattern-loader

Ansible playbooks to seed seeding content into AAP.
Playbooks create in AAP objects needed for Ansible Patterns -
execution environment, project, job templates etc.

## Run from AAP

This is how it is used as part of ansible experience.

## Run from cli

For local development only.

Add vars needed to access AAP

```
cat aap.yml
---
aap_hostname: https://AAP_IP
aap_validate_certs: false
# controller_oauthtoken:
aap_username: admin
aap_password: todo
```

Install needed collections:

```
cat requirements.yml 
collections:
  - name: ansible.platform
  - name: ansible.hub
  - name: ansible.controller
  - name: ansible.eda
  - name: infra.aap_configuration
  - name: infra.ee_utilities
  - name: containers.podman

ansible-galaxy collection install -r requirements.yml
pip install ansible-builder
```

Run

```
ansible-playbook -e@aap.yml -e seed_usecase=rhel seed_portal_content.yml
ansible-playbook -e@aap.yml -e seed_usecase=network seed_portal_content.yml
```

## Prepare execution environment

An execution environment image is needed to run the `seed_portal_content.yml` in AAP.
Follow [exec_env/README.md](exec_env/README.md) to build one.
