# Ansible Gotchas

1. `ansible-playbook -i hosts_one playbooks/structure.yml -v`

    Notes:
        - Checkout the following:
            group_vars
            roles
                structure
                    defaults
                    meta
                    tasks
                    templates
            playbooks
            hosts_one
