# ACI Ansible Configuration

This project contains Ansible playbooks to create multiple tenants and VRFs in Cisco ACI.

## Prerequisites

1. Install Ansible:
```bash
pip install ansible
```

2. Install Cisco ACI Collection:
```bash
ansible-galaxy collection install cisco.aci
```

## File Structure
```
aci_ansible/
├── inventory
├── vars/
│   └── aci_credentials.yml
└── create_aci_resources.yml
```

## Setup Instructions

1. Create project directory:
```bash
mkdir aci_ansible
cd aci_ansible
```

2. Create the following files with provided content:
   - `inventory`
   - `vars/aci_credentials.yml`
   - `create_aci_resources.yml`

3. Update credentials in `vars/aci_credentials.yml` with your APIC details.

## Running the Playbook

1. Test connectivity:
```bash
ansible apic -i inventory -m ping
```

2. Run the playbook:
```bash
ansible-playbook -i inventory create_aci_resources.yml
```

## What Gets Created
- 10 tenants (test-tenant-1 through test-tenant-10)
- 10 VRFs (test-vrf-1 through test-vrf-10, one in each tenant)

## Cleanup

To remove the created resources, change `state: present` to `state: absent` in the playbook and run it again.

## Troubleshooting
- Ensure all files are in the correct directory structure
- Verify APIC credentials in vars/aci_credentials.yml
- Check that APIC URL includes "https://"
- Make sure Cisco ACI collection is installed