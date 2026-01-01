# Homelab

Personal homelab repository for infrastructure configuration, application stacks, and operational runbooks.

This repo is organized to keep “desired configuration” (what should be deployed) in Git, while treating runtime state (databases, app metadata) as backups, not versioned files.

## Folder structure

- [README.md](README.md) — repo overview and navigation
- [CHANGELOG.md](CHANGELOG.md) — notable changes #TODO
- [.gitignore](.gitignore) Preview

- [.editorconfig](.editorconfig) #TODO
- [Makefile](Makefile) — common tasks #TODO

<details>
<summary><a href="docs/">docs/</a> — architecture, network, storage, runbooks</summary>

- [architecture.md](docs/architecture.md) #TODO
- [network.md](docs/network.md) #TODO
- [storage.md](docs/storage.md) #TODO
- [runbooks/](docs/runbooks/) #TODO
  - [rebuild-servarr-vm.md](docs/runbooks/rebuild-servarr-vm.md) #TODO
  - [restore-jellyfin.md](docs/runbooks/restore-jellyfin.md) #TODO
  - [gpu-passthrough-notes.md](docs/runbooks/gpu-passthrough-notes.md) #TODO
  </details>

<details>
<summary><a href="inventory/">inventory/</a> — desired hosts, networks, DNS</summary>

- [sites/](inventory/sites/) #TODO
  - [home/](inventory/sites/home/) #TODO
    - [hosts.yaml](inventory/sites/home/hosts.yaml) #TODO
    - [vars.yaml](inventory/sites/home/vars.yaml) #TODO
- [ipam/](inventory/ipam/) #TODO
  - [networks.yaml](inventory/ipam/networks.yaml) #TODO
  - [dns-records.yaml](inventory/ipam/dns-records.yaml) #TODO
  </details>

<details>
<summary><a href="platform/">platform/</a> — Proxmox and TrueNAS configuration references</summary>

- [proxmox/](platform/proxmox/) #TODO
  - [nodes/](platform/proxmox/nodes/) #TODO
    - [pve-guide/](platform/proxmox/nodes/pve-guide/) #TODO
      - [post-install.md](platform/proxmox/nodes/pve-guide/post-install.md) #TODO
      - [sysctl.conf](platform/proxmox/nodes/pve-guide/sysctl.conf) #TODO
      - [modprobe.d/](platform/proxmox/nodes/pve-guide/modprobe.d/) #TODO
      - [systemd/](platform/proxmox/nodes/pve-guide/systemd/) #TODO
  - [lxc/](platform/proxmox/lxc/) #TODO
    - [1013-jellyfin/](platform/proxmox/lxc/1013-jellyfin/) #TODO
      - [config.conf](platform/proxmox/lxc/1013-jellyfin/config.conf)  #TODO
      - [mounts.md](platform/proxmox/lxc/1013-jellyfin/mounts.md) #TODO
      - [gpu.md](platform/proxmox/lxc/1013-jellyfin/gpu.md) #TODO
  - [scripts/](platform/proxmox/scripts/) #TODO
    - [snapshot.sh](platform/proxmox/scripts/snapshot.sh) #TODO
    - [vzdump-wrapper.sh](platform/proxmox/scripts/vzdump-wrapper.sh) #TODO
- [truenas/](platform/truenas/) #TODO
  - [datasets.yaml](platform/truenas/datasets.yaml) #TODO
  - [smb/](platform/truenas/smb/) #TODO
    - [shares.yaml](platform/truenas/smb/shares.yaml) #TODO
  - [notes.md](platform/truenas/notes.md) #TODO
  </details>

<details>
<summary><a href="apps/">apps/</a> — application stacks by runtime</summary>

- [docker/](apps/docker/) #TODO
  - [stacks/](apps/docker/stacks/) #TODO
    - [servarr/](apps/docker/stacks/servarr/) #TODO
      - [compose.yaml](apps/docker/stacks/servarr/compose.yaml)
      - [compose.override.example.yaml](apps/docker/stacks/servarr/compose.override.example.yaml) #TODO
      - [env.example](apps/docker/stacks/servarr/env.example) #TODO
      - [secrets.sops.yaml](apps/docker/stacks/servarr/secrets.sops.yaml) #TODO
      - [volumes.md](apps/docker/stacks/servarr/volumes.md) #TODO
      - [notes.md](apps/docker/stacks/servarr/notes.md) #TODO
      - [configs/](apps/docker/stacks/servarr/configs/) #TODO
        - [prowlarr/](apps/docker/stacks/servarr/configs/prowlarr/) #TODO
        - [gluetun/](apps/docker/stacks/servarr/configs/gluetun/) #TODO
        - [traefik-or-nginx/](apps/docker/stacks/servarr/configs/traefik-or-nginx/) #TODO
    - [jellyfin-aux/compose.yaml](apps/docker/stacks/jellyfin-aux/compose.yaml) #TODO
    - [observability/compose.yaml](apps/docker/stacks/observability/compose.yaml) #TODO
    - [observability/env.example](apps/docker/stacks/observability/env.example) #TODO
- [lxc-services/](apps/lxc-services/) #TODO
  - [jellyfin/](apps/lxc-services/jellyfin/) - [install.md](apps/lxc-services/jellyfin/install.md) - [backups.md] #TODO (apps/lxc-services/jellyfin/backups.md)
  </details>

<details>
<summary><a href="automation/">automation/</a> — infra-as-code and config management</summary>

- [ansible/](automation/ansible/) #TODO
  - [inventories/](automation/ansible/inventories/) #TODO
    - [home/](automation/ansible/inventories/home/) #TODO
      - [hosts.ini](automation/ansible/inventories/home/hosts.ini) #TODO
      - [group_vars/](automation/ansible/inventories/home/group_vars/) #TODO
      - [host_vars/](automation/ansible/inventories/home/host_vars/) #TODO
  - [roles/](automation/ansible/roles/) #TODO
  - [playbooks/](automation/ansible/playbooks/) #TODO
    - [site.yml](automation/ansible/playbooks/site.yml) #TODO
    - [docker-host.yml](automation/ansible/playbooks/docker-host.yml) #TODO
    - [proxmox-node.yml](automation/ansible/playbooks/proxmox-node.yml) #TODO
- [terraform/](automation/terraform/) #TODO
  - [cloudflare/](automation/terraform/cloudflare/) #TODO
  </details>

<details>
<summary><a href="secrets/">secrets/</a> — encryption docs and public recipients</summary>

- [README.md](secrets/README.md) #TODO
- [age/](secrets/age/) #TODO
  - [recipients.txt](secrets/age/recipients.txt) #TODO
  </details>

<details>
<summary><a href="scripts/">scripts/</a> — local helper scripts</summary>

- [apply.sh](scripts/apply.sh) #TODO
- [export-cloudflare.sh](scripts/export-cloudflare.sh) #TODO
</details>

<details>
<summary><a href="backups/">backups/</a> — backup manifests and retention</summary> 

- [manifests/](backups/manifests/) #TODO
  - [jellyfin.md](backups/manifests/jellyfin.md) #TODO
  - [servarr.md](backups/manifests/servarr.md) #TODO
  </details>

<details>
<summary><a href=".github/">.github/</a> — CI workflows</summary>

- [workflows/](.github/workflows/) #TODO
  - [lint.yaml](.github/workflows/lint.yaml) #TODO
  </details>

## Notes

- Do not commit secrets in plaintext. Use SOPS/age (preferred) or Ansible Vault.
- Runtime state (databases, app metadata, media libraries) should be backed up separately; Git tracks only “desired configuration”.
