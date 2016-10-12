# Ansible Gotchas, Tricks and Tools

## Synopsis

**TITLE** Ansible Gotchas, Tricks and Tools

**DESCRIPTION** Ansible is a great configuration management tool. However like all tools there are certain aspects of it one must be aware of to fully utilize its capabilities and not to get stuck when a problem comes up. In this presentation we walk through examples of issues that were faced and solutions that was come up with. We will also be taking a look on some tools we can use to have a faster development cycle.

**ABSTRACT** Ansible documentation is well written however there are certain aspects of it that may not be immediately apparent to the developer. To this extent we will be go over the following subjects:

- Structure of an Ansible project
- Roles structure
- Playbook structure
- Playbook vs Role
- Host files (Parents, Children and Dynamic hosts)
- Variables and their scopes
- Roles and dependencies
- Templates
- Conditionals
- Tools: ansible-linter

## Demonstration

1. `ansible-playbook -i hosts_one playbooks/structure.yml -v`

    Notes:
        - Checkout the following:
        ```
            group_vars
            roles
                structure
                    defaults
                    meta
                    tasks
                    templates
            playbooks
            hosts_one
        ```
2. Move roles before task.
    ```
        ansible-playbook -i hosts_one playbooks/structure.yml -v
    ```
    Gotchas:
        - Roles run before tasks

3. Hosts and host groups
    ```
        ansible-playbook -i hosts_one playbooks/hosts.yml -v
        ansible-playbook -i hosts.d playbooks/hosts.yml -v
        ansible-playbook playbooks/hosts.yml -v
    ```
    Gotchas:
        - If using directory for hosts naming of host files are important. Example: change allhosts to zhosts
        - Just because you specified hosts in a sequence doesn't mean runs will be in a sequence
        - Specify your hosts file otherwise be ready to get the unexpected (i.e. /etc/ansible/hosts might get picked up!)
