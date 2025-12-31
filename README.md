# Homelab

Personal homelab repository for infrastructure configuration, application stacks, and operational runbooks.

This repo is organized to keep “desired configuration” (what should be deployed) in Git, while treating runtime state (databases, app metadata) as backups, not versioned files.

## Folder structure

```text
homelab/
  README.md
  CHANGELOG.md                      # optional but useful for “what changed”

  docs/
    architecture.md
    network.md                       # subnets, VLANs, DNS, reverse proxy approach
    storage.md                       # TrueNAS datasets/shares + mount conventions
    runbooks/
      restore-jellyfin.md
      rebuild-servarr-vm.md
      gpu-passthrough-notes.md

  inventory/
    sites/
      home/
        hosts.yaml                   # canonical host list + roles
        vars.yaml                    # site-wide vars (domains, LAN, TZ, etc.)
    ipam/
      networks.yaml                  # subnets, reservations, important IPs
      dns-records.yaml               # intended Cloudflare/local DNS records

  platform/
    proxmox/
      nodes/
        pve-guide/
          post-install.md
          sysctl.conf
          modprobe.d/
          systemd/
      lxc/
        1013-jellyfin/
          config.conf                # sanitized CT config (no secrets)
          mounts.md                  # bind-mount intent and mapping
          gpu.md                     # device/node requirements + troubleshooting
      scripts/
        snapshot.sh
        vzdump-wrapper.sh

    truenas/
      datasets.yaml                  # desired dataset layout
      smb/
        shares.yaml                  # intended SMB share config
      notes.md

  apps/
    docker/
      stacks/
        servarr/
          compose.yaml
          compose.override.example.yaml
          env.example
          secrets.sops.yaml          # encrypted secrets (recommended)
          volumes.md                 # host paths + mount intent
          notes.md                   # deploy/upgrade notes
          configs/                   # only if you manage config-as-files
            prowlarr/
            gluetun/
            traefik-or-nginx/
        jellyfin-aux/
          compose.yaml               # sidecars/exporters/etc.
        observability/
          compose.yaml
          env.example

    lxc-services/
      jellyfin/
        install.md                   # if managed directly inside an LXC
        backups.md

  automation/
    ansible/
      inventories/
        home/
          hosts.ini
          group_vars/
          host_vars/
      roles/
      playbooks/
        site.yml
        docker-host.yml
        proxmox-node.yml
    terraform/
      cloudflare/                    # optional (DNS as code, etc.)

  secrets/
    README.md                        # how secrets are encrypted/decrypted
    age/
      recipients.txt                 # public recipients (safe to commit)

  scripts/
    apply.sh                         # wrappers (lint + deploy)
    export-cloudflare.sh             # if you keep DNS as code

  backups/
    manifests/
      jellyfin.md                    # what’s backed up + where + retention
      servarr.md

  .github/
    workflows/
      lint.yaml

  .gitignore
  .editorconfig
  Makefile                           # or Taskfile.yml
