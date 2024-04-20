# Atacar a grupos o servidores individuales

### Scaffolding

- ansible /
  - inventory
  - playbooks /
    - ping.yml
    - hello_world.yml
    - install_docker.yml

## Grupos especiales

- all
- ungrouped

### Ping al servidor db
```bash
ansible -i inventory db_servers -m ping
ansible -i inventory db_servers -m playbooks/ping.yml -l db1
```


### Probar play-book
```bash
    ansible-playbook -i inventory playbooks/ping.yml
```

### Distintas flags
    
```bash
    ansible-playbook --syntax-check -i inventory playbooks/hello_world.yml

    ansible-playbook --list-hosts -i inventory playbooks/hello_world.yml

    ansible-playbook --list-tasks -i inventory playbooks/hello_world.yml

    ansible-playbook --check -i inventory playbooks/hello_world.yml

    ansible-playbook --step -i inventory playbooks/install_docker.yml
```