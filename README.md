# Homelab

A personal homelab project made as a hobby

## Folder Structure

´´homelab/
README.md
CHANGELOG.md # optional but useful for “what changed”
docs/
architecture.md
network.md # subnets, VLANs, DNS, reverse proxy approach
storage.md # TrueNAS datasets/shares + mount conventions
runbooks/
restore-jellyfin.md
rebuild-servarr-vm.md
gpu-passthrough-notes.md
inventory/
sites/
home/
hosts.yaml # canonical host list + roles
vars.yaml # site-wide vars (domains, LAN, TZ, etc.)
ipam/
networks.yaml # subnets, reservations, important IPs
dns-records.yaml # what you intend Cloudflare/local DNS to have
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
config.conf # sanitized CT config (no secrets)
mounts.md # what gets bind-mounted and why
gpu.md # device node requirements, troubleshooting
scripts/
snapshot.sh
vzdump-wrapper.sh
truenas/
datasets.yaml # desired dataset layout
smb/
shares.yaml # desired share config (documented)
notes.md
apps/
docker/
stacks/
servarr/
compose.yaml
compose.override.example.yaml
env.example
secrets.sops.yaml # encrypted secrets (recommended)
volumes.md # exact host paths + mount intent
notes.md # “how to deploy/upgrade”
configs/
prowlarr/ # only if you manage config-as-files
gluetun/
traefik-or-nginx/
jellyfin-aux/
compose.yaml # if you run any sidecars, exporters, etc.
observability/
compose.yaml
env.example
lxc-services/
jellyfin/
install.md # if you manage as “pet” CT, document steps
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
terraform/ # optional (Cloudflare, etc.)
cloudflare/
secrets/
README.md # how secrets are encrypted/decrypted
age/
recipients.txt # public recipients (safe to commit)
scripts/
apply.sh # “one command” wrappers (lint + deploy)
export-cloudflare.sh # if you keep DNS as code
backups/
manifests/
jellyfin.md # what’s backed up + where + retention
servarr.md
.github/
workflows/
lint.yaml
.gitignore´´
.editorconfig
Makefile # or Taskfile.yml
