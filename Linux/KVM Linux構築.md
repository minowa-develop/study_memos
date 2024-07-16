# KVM Linux構築

```bash
#!/bin/bash

# tool install
dnf install qemu-kvm libvirt virt-install virt-viewer -y

# service start
for drv in qemu network nodedev nwfilter secret storage interface; do systemctl start virt${drv}d{,-ro,-admin}.socket; done

# KVM validate
virt-host-validate

# gest-os install

# gest-os constant
VM_NAME=demo-guest1
MEM=1024
CPU_CORE_COUNT=2
STORAGE_SIZE=2 # Unit=GiB
OS_VAR=ubuntu22.04 # virt-install --osinfo list
CDROM_PATH=/var/iso/ubuntu-22.04.3-live-server-amd64.iso

virt-install \
--name "${VM_NAME}" --memory "${MEM}" \
--vcpus "${CPU_CORE_COUNT}" --disk size="${STORAGE_SIZE}" --os-variant "${OS_VAR}" \
--cdrom "${CDROM_PATH}"
```
