#!/bin/bash

# Directory for temporary files
TEMP_DIR="/tmp/wireguard_keys"
mkdir -p $TEMP_DIR

# Generate a new private key and corresponding public key
wg genkey | tee "$TEMP_DIR/privatekey" | wg pubkey > "$TEMP_DIR/publickey"

# Load the keys into variables
PRIVATE_KEY=$(cat "$TEMP_DIR/privatekey")

# Array of VPN servers: Name, Endpoint, and Server's Public Key
VPN_SERVERS=(
    "ProtonVPN vpn1.protonvpn.com:51820 <ProtonVPNPublicKey>"
    "VPNJantit vpn2.vpnjantit.com:51820 <VPNJantitPublicKey>"
    "FreeVPN vpn3.freevpn.com:51820 <FreeVPNPublicKey>"
)

# Randomly select a VPN server from the list
SELECTED_SERVER=${VPN_SERVERS[$RANDOM % ${#VPN_SERVERS[@]}]}

# Split the selected server's details into variables
SERVER_NAME=$(echo $SELECTED_SERVER | awk '{print $1}')
SERVER_ENDPOINT=$(echo $SELECTED_SERVER | awk '{print $2}')
SERVER_PUBLIC_KEY=$(echo $SELECTED_SERVER | awk '{print $3}')

# Path to the WireGuard configuration file
WG_CONF="/etc/wireguard/wg0.conf"

# Detect the primary network interface
PRIMARY_INTERFACE=$(ip route | grep default | awk '{print $5}')

# Disable the primary network interface for security
if [ -n "$PRIMARY_INTERFACE" ]; then
    echo "Disabling primary network interface: $PRIMARY_INTERFACE"
    ip link set dev $PRIMARY_INTERFACE down
else
    echo "No primary network interface detected!"
    exit 1
fi

# Create a new WireGuard configuration file
cat <<EOL > $WG_CONF
[Interface]
PrivateKey = $PRIVATE_KEY
Address = 10.0.0.2/24
DNS = 1.1.1.1

[Peer]
PublicKey = $SERVER_PUBLIC_KEY
Endpoint = $SERVER_ENDPOINT
AllowedIPs = 0.0.0.0/0
PersistentKeepalive = 25
EOL

# Print information about the selected server
echo "Connecting to $SERVER_NAME at $SERVER_ENDPOINT"

# Bring down any existing WireGuard interface
wg-quick down wg0 2>/dev/null

# Bring up the new WireGuard interface
wg-quick up wg0

# Optional: Re-enable the primary network interface after disconnecting from WireGuard
# Uncomment the following lines if needed:
# echo "Re-enabling primary network interface: $PRIMARY_INTERFACE"
# ip link set dev $PRIMARY_INTERFACE up
