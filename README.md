# Homelab

Personal homelab repository for infrastructure configuration, application stacks, and operational runbooks.

This repo is organized to keep “desired configuration” (what should be deployed) in Git, while treating runtime state (databases, app metadata) as backups, not versioned files.

## Folder structure (clickable)

- **[docs/](./docs/)**
  - [architecture.md](./docs/architecture.md)
  - [network.md](./docs/network.md)
  - [storage.md](./docs/storage.md)
  - **[runbooks/](./docs/runbooks/)**
    - [restore-jellyfin.md](./docs/runbooks/restore-jellyfin.md)
    - [rebuild-servarr-vm.md](./docs/runbooks/rebuild-servarr-vm.md)
    - [gpu-passthrough-notes.md](./docs/runbooks/gpu-passthrough-notes.md)

- **[inventory/](./inventory/)**
  - **[sites/](./inventory/sites/)**
    - **[home/](./inventory/sites/home/)**
      - [hosts.yaml](./inventory/sites/home/hosts.yaml)
      - [vars.yaml](./inventory/sites/home/vars.yaml)
  - **[ipam/](./inventory/ipam/)**
    - [networks.yaml](./inventory/ipam/networks.yaml)
    - [dns-records.yaml](./inventory/ipam/dns-records.yaml)

- **[platform/](./platform/)**
  - **[proxmox/](./platform/proxmox/)**
    - **[nodes/](./platform/proxmox/nodes/)**
      - **[pve-guide/](./platform/proxmox/nodes/pve-guide/)**
        - [post-install.md](./platform/proxmox/nodes/pve-guide/post-install.md)
        - [sysctl.conf](./platform/proxmox/nodes/pve-guide/sysctl.conf)
        - **[modprobe.d/](./platform/proxmox/nodes/pve-guide/modprobe.d/)**
        - **[systemd/](./platform/proxmox/nodes/pve-guide/systemd/)**
    - **[lxc/](./platform/proxmox/lxc/)**
      - **[1013-jellyfin/](./platform/proxmox/lxc/1013-jellyfin/)**
        - [config.conf](./platform/proxmox/lxc/1013-jellyfin/config.conf)
        - [mounts.md](./platform/proxmox/lxc/1013-jellyfin/mounts.md)
        - [gpu.md](./platform/proxmox/lxc/1013-jellyfin/gpu.md)
    - **[scripts/](./platform/proxmox/scripts/)**
      - [snapshot.sh](./platform/proxmox/scripts/snapshot.sh)
      - [vzdump-wrapper.sh](./platform/proxmox/scripts/vzdump-wrapper.sh)

  - **[truenas/](./platform/truenas/)**
    - [datasets.yaml](./platform/truenas/datasets.yaml)
    - [notes.md](./platform/truenas/notes.md)
    - **[smb/](./platform/truenas/smb/)**
      - [shares.yaml](./platform/truenas/smb/shares.yaml)

- **[apps/](./apps/)**
  - **[docker/](./apps/docker/)**
    - **[stacks/](./apps/docker/stacks/)**
      - **[servarr/](./apps/docker/stacks/servarr/)**
        - [compose.yaml](./apps/docker/stacks/servarr/compose.yaml)
        - [compose.override.example.yaml](./apps/docker/stacks/servarr/compose.override.example.yaml)
        - [env.example](./apps/docker/stacks/servarr/env.example)
        - [secrets.sops.yaml](./apps/docker/stacks/servarr/secrets.sops.yaml)
        - [volumes.md](./apps/docker/stacks/servarr/volumes.md)
        - [notes.md](./apps/docker/stacks/servarr/notes.md)
        - **[configs/](./apps/docker/stacks/servarr/configs/)**
          - **[prowlarr/](./apps/docker/stacks/servarr/configs/prowlarr/)**
          - **[gluetun/](./apps/docker/stacks/servarr/configs/gluetun/)**
          - **[traefik-or-nginx/](./apps/docker/stacks/servarr/configs/traefik-or-nginx/)**
      - **[jellyfin-aux/](./apps/docker/stacks/jellyfin-aux/)**
        - [compose.yaml](./apps/docker/stacks/jellyfin-aux/compose.yaml)
      - **[observability/](./apps/docker/stacks/observability/)**
        - [compose.yaml](./apps/docker/stacks/observability/compose.yaml)
        - [env.example](./apps/docker/stacks/observability/env.example)

  - **[lxc-services/](./apps/lxc-services/)**
    - **[jellyfin/](./apps/lxc-services/jellyfin/)**
      - [install.md](./apps/lxc-services/jellyfin/install.md)
      - [backups.md](./apps/lxc-services/jellyfin/backups.md)

- **[automation/](./automation/)**
  - **[ansible/](./automation/ansible/)**
    - **[inventories/](./automation/ansible/inventories/)**
      - **[home/](./automation/ansible/inventories/home/)**
        - [hosts.ini](./automation/ansible/inventories/home/hosts.ini)
        - **[group_vars/](./automation/ansible/inventories/home/group_vars/)**
        - **[host_vars/](./automation/ansible/inventories/home/host_vars/)**
    - **[roles/](./automation/ansible/roles/)**
    - **[playbooks/](./automation/ansible/playbooks/)**
      - [site.yml](./automation/ansible/playbooks/site.yml)
      - [docker-host.yml](./automation/ansible/playbooks/docker-host.yml)
      - [proxmox-node.yml](./automation/ansible/playbooks/proxmox-node.yml)

  - **[terraform/](./automation/terraform/)**
    - **[cloudflare/](./automation/terraform/cloudflare/)**

- **[secrets/](./secrets/)**
  - [README.md](./secrets/README.md)
  - **[age/](./secrets/age/)**
    - [recipients.txt](./secrets/age/recipients.txt)

- **[scripts/](./scripts/)**
  - [apply.sh](./scripts/apply.sh)
  - [export-cloudflare.sh](./scripts/export-cloudflare.sh)

- **[backups/](./backups/)**
  - **[manifests/](./backups/manifests/)**
    - [jellyfin.md](./backups/manifests/jellyfin.md)
    - [servarr.md](./backups/manifests/servarr.md)

- **[.github/](./.github/)**
  - **[workflows/](./.github/workflows/)**
    - [lint.yaml](./.github/workflows/lint.yaml)

- [CHANGELOG.md](./CHANGELOG.md)
- [.gitignore](./.gitignore)
- [.editorconfig](./.editorconfig)
- [Makefile](./Makefile)

## Notes

- Do not commit secrets in plaintext. Use SOPS/age (preferred) or Ansible Vault.
- Runtime state (databases, app metadata, media libraries) should be backed up separately; Git tracks only “desired configuration”.
