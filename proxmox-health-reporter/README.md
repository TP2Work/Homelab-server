Collects system and VM health metrics from a Proxmox server
and sends a daily email report.

Metrics include
- CPU load and temperatures
- Memory usage
- Disk usage and SMART health
- ZFS pool status and I/O
- VM resource usage (CPU via QEMU process)

Architecture
- Bash script (/usr/local/bin/proxmox-health)
- Cron job (daily execution)
- Postfix (SMTP relay via Gmail)
- Email delivery (external inbox)

Requirements
- Proxmox VE
- Postfix configured with SMTP relay
- mailutils
- smartmontools
- lm-sensors
