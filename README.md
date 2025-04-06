```markdown
# Infrastructure Ansible Playbooks

This repository contains Ansible playbooks for deploying infrastructure components including:

- SLURM Cluster (Database, Control, and Compute nodes)
- OpenLDAP Server

## SLURM Components

### SLURM Database Server
- MariaDB/MySQL database setup
- Munge authentication configuration
- SLURM database daemon configuration

### SLURM Control Server
- Munge authentication configuration
- SLURM controller daemon setup
- CGroup configuration

### SLURM Compute Nodes
- Munge authentication configuration
- SLURM compute daemon setup

### OpenLDAP Server
- Complete OpenLDAP installation and configuration
- User and group management
- LDAP authentication setup

## Directory Structure

 ```

```

.
├── group_vars/
│   └── all.yml
├── roles/
│   ├── slurmdbd/
│   ├── slurmctld/
│   ├── compute/
│   └── openldap/
├── inventory/
│   └── hosts
├── slurmdbd.yml
├── slurmctld.yml
├── compute.yml
└── openldap.yml

```plaintext

## Usage

### SLURM Deployment

1. Configure your inventory in `inventory/hosts`
2. Customize variables in `group_vars/all.yml`
3. Deploy in sequence:

```bash
# 1. Deploy SLURM Database Server
ansible-playbook -i inventory/hosts slurmdbd.yml

# 2. Deploy SLURM Control Server
ansible-playbook -i inventory/hosts slurmctld.yml

# 3. Deploy SLURM Compute Nodes
ansible-playbook -i inventory/hosts compute.yml
 ```

```

### OpenLDAP Deployment
1. Configure your inventory in inventory/hosts (add to services group)
2. Deploy OpenLDAP:
```bash
# Deploy OpenLDAP Server
ansible-playbook -i inventory/hosts openldap.yml
 ```

```

You can customize OpenLDAP settings in the playbook:

```yaml
vars:
  ldap_domain: "example.com"
  ldap_organization: "Example Org"
  ldap_root_dn: "cn=admin,dc=example,dc=com"
  ldap_base_dn: "dc=example,dc=com"
  ldap_admin_password: "SecurePassword"
 ```

```

## Requirements
- Ansible 2.9 or higher
- Target systems running supported Linux distribution (RHEL/CentOS/Rocky Linux)
- SSH access to all nodes
- Sudo privileges on target systems
