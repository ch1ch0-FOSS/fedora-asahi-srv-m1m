# asahi-srv-m1m

Fedora Asahi Linux server blueprint for srv-m1m on Apple M1 Mac mini.

This repository defines the high-level inventory and playbook structure used to configure the server.
It delegates reusable roles and tooling to dedicated repositories:

- Ansible roles and shared playbooks: https://github.com/ch1ch0-FOSS/ansible-playbooks
- Disaster recovery tooling: https://github.com/ch1ch0-FOSS/disaster-recovery-toolkit
- Operator environment (dotfiles, terminal workflow): https://github.com/ch1ch0-FOSS/dotfiles-terminal-workflow
- Narrative case studies and design notes: https://github.com/ch1ch0-FOSS/infrastructure-case-studies

## Usage (blueprint only)

1. Clone this repository and ansible-playbooks.
2. Copy `inventory/example` to your own inventory and adjust hostnames and groups.
3. Define real variables in `group_vars/` and `host_vars/` on your own infrastructure (not in this public repo).
4. Run your playbooks from ansible-playbooks using this inventory structure as a reference.
# Test sync
