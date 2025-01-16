grep -E 'SAP[A-Z0-9]{3}|HDB[A-Z0-9]{3}|ASE[A-Z0-9]{3}' /proc/*/cmdline | cut -d/ -f3 | sort -u
