# OpenOctopus Ansible Maintenance Guide

## Project State

- Repository: `open-octopus/openoctopus-ansible`
- Category: self-hosted OpenOctopus deployment automation
- Runtime target: Debian/Ubuntu server managed through Ansible
- Main playbooks: `deploy.yml`, `update.yml`, `backup.yml`, `restore.yml`

## Before Editing

- Treat inventory and variables as secret-bearing files. Do not commit `inventory.yml`, `vars.yml`, vault passwords, or real API keys.
- Prefer dry runs before changing roles that affect firewall, Docker, Tailscale, or backup behavior.
- Preserve idempotency in tasks and handlers.

## Useful Commands

- Install roles: `ansible-galaxy install -r requirements.yml`
- Syntax check: `ansible-playbook deploy.yml -i inventory.example.yml --syntax-check`
- Dry run: `ansible-playbook deploy.yml -i inventory.yml -e @vars.yml --check --diff`
- Deploy: `ansible-playbook deploy.yml -i inventory.yml -e @vars.yml`

## Environment

- Use `vars.example.yml` and `inventory.example.yml` as canonical templates.
- `.env.example` documents optional shell exports for operators and CI wrappers.

## Deployment Notes

- See `DEPLOYMENT.md` before touching firewall, Tailscale, backup, or Docker roles.
- Validate public ports after deployment; only SSH and Tailscale should be reachable by default.
