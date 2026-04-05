#!/bin/bash

echo "Proxmox Health Report for $(hostname)"
echo "Generated: $(date)"
echo ""

echo "=== SYSTEM LOAD ==="
uptime
echo ""

echo "=== CPU TEMPERATURES ==="
sensors
echo ""

echo "=== SMART HEALTH SUMMARY ==="
for disk in /dev/sd?; do
    echo "Device: $disk"
    smartctl -H $disk 2>/dev/null | grep "SMART overall-health"
    echo ""
done

echo "=== DISK USAGE (/) ==="
df -h /
echo ""

echo "=== MEMORY ==="
free -h
echo ""

echo "=== ZFS STATUS ==="
zpool status
echo ""

echo "=== ZFS I/O ==="
zpool iostat -v 1 3
echo ""

echo "=== VM RESOURCE USAGE ==="
NODE="$(hostname)"
for vmid in $(qm list | awk 'NR>1 {print $1}'); do
#   echo "VMID: $vmid"
   # Retrieving the PID of the VM with ps and top
   PID=$(ps -eo pid,cmd | grep "[i]d $vmid" | awk '{print $1}')   # had to make sure that the PID of grep doesn't also show up when querying 
   CPU=$(top -bn2 -p $PID | tail -1 | awk '{print $9}')
   echo "CPU Usage: ${CPU}%"

   # Query current status via pvesh (JSON) and parse with jq
   data=$(pvesh get /nodes/"$NODE"/qemu/"$vmid"/status/current --output-format text)
   echo "$data"
done
