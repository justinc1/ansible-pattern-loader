# Ansible Pattern Loader Execution Environment

To build this EE:

```
cp -i exec_env/secrets.yml.template exec_env/secrets.yml
nano exec_env/secrets.yml

ansible-playbook -e @exec_env/secrets.yml exec_env/build_ansible_pattern_loader_ee.yml
```
