# SLURM Cluster Ansible Playbooks

This repository contains Ansible playbooks for deploying a complete SLURM cluster with the following components:

- SLURM Database Server (slurmdbd)
- SLURM Control Server (slurmctld)
- SLURM Compute Nodes

## Components

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

## Directory Structure

```
.
├── group_vars/
│   └── all.yml
├── roles/
│   ├── slurmdbd/
│   ├── slurmctld/
│   └── compute/
├── inventory/
│   └── hosts
├── slurmdbd.yml
├── slurmctld.yml
└── compute.yml
```

## Usage

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

## Requirements

- Ansible 2.9 or higher
- Target systems running supported Linux distribution
- SSH access to all nodes
- Sudo privileges on target systems#   p l a y b o o k s - s l u r m  
 