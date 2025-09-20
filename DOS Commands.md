# Networking DOS Commands Reference

A comprehensive list of essential Windows command-line networking utilities for network troubleshooting, configuration, and diagnostics.

## Basic IP Configuration Commands

### `ipconfig`
**Description**: Displays basic IP address information of the computer.  
**Syntax**: `ipconfig`  
**Use**: Shows IPv4, subnet mask, and default gateway.

### `ipconfig /all`
**Description**: Shows detailed network configuration including MAC address, DNS, DHCP status.  
**Syntax**: `ipconfig /all`  
**Use**: Helpful for complete diagnostic info.

### `ipconfig /release`
**Description**: Releases the current IP address assigned to the machine.  
**Syntax**: `ipconfig /release`  
**Use**: Used when renewing or changing IPs.

### `ipconfig /renew`
**Description**: Requests a new IP address from the DHCP server.  
**Syntax**: `ipconfig /renew`  
**Use**: Obtains fresh IP configuration after release.

### `ipconfig /flushdns`
**Description**: Clears the DNS resolver cache.  
**Syntax**: `ipconfig /flushdns`  
**Use**: Resolves DNS-related issues by clearing cached entries.

### `ipconfig /displaydns`
**Description**: Shows the contents of the DNS resolver cache.  
**Syntax**: `ipconfig /displaydns`  
**Use**: Views cached DNS records.

## Network Diagnostic Commands

### `ping`
**Description**: Tests connectivity to another IP or domain.  
**Syntax**: `ping [hostname/IP]`  
**Use**: Checks if a host is reachable and measures response time.

### `tracert`
**Description**: Traces the route packets take to reach a destination.  
**Syntax**: `tracert [hostname/IP]`  
**Use**: Identifies network delays or unreachable points.

### `pathping`
**Description**: Combines features of ping and tracert with more detailed statistics.  
**Syntax**: `pathping [hostname/IP]`  
**Use**: Provides comprehensive route analysis with packet loss statistics.

### `nslookup`
**Description**: Queries DNS servers to obtain domain name or IP address information.  
**Syntax**: `nslookup [hostname]` or `nslookup [IP address]`  
**Use**: Troubleshoots DNS resolution problems.

## Connection and Port Management

### `netstat`
**Description**: Displays active network connections and listening ports.  
**Syntax**: `netstat`  
**Use**: Checks open connections and network statistics.

### `netstat -a`
**Description**: Shows all connections and listening ports.  
**Syntax**: `netstat -a`  
**Use**: Views all active TCP and UDP connections.

### `netstat -b`
**Description**: Displays the executable involved in creating each connection.  
**Syntax**: `netstat -b`  
**Use**: Identifies which applications are using network connections.

### `netstat -n`
**Description**: Shows addresses and port numbers in numerical form.  
**Syntax**: `netstat -n`  
**Use**: Faster display without DNS resolution.

### `telnet`
**Description**: Tests connectivity to specific ports.  
**Syntax**: `telnet [hostname] [port]`  
**Use**: Checks if a specific port is open and accessible.

## Routing Commands

### `route`
**Description**: Displays or modifies the IP routing table.  
**Syntax**: `route print` or `route add [destination]`  
**Use**: Manages manual routing paths.

### `route print`
**Description**: Displays the current IP routing table.  
**Syntax**: `route print`  
**Use**: Views all configured routes.

### `route add`
**Description**: Adds a persistent route to the routing table.  
**Syntax**: `route add [destination] mask [subnetmask] [gateway]`  
**Use**: Creates static routes for specific networks.

## Advanced Networking Commands

### `arp`
**Description**: Displays and modifies the IP-to-Physical address translation tables.  
**Syntax**: `arp -a`  
**Use**: Views ARP cache entries.

### `netsh`
**Description**: Network Shell utility for configuring various network components.  
**Syntax**: `netsh [context] [command]`  
**Use**: Advanced network configuration and troubleshooting.

### `getmac`
**Description**: Displays the MAC address for network adapters.  
**Syntax**: `getmac`  
**Use**: Retrieves physical addresses of network interfaces.

### `nbtstat`
**Description**: Displays NetBIOS over TCP/IP statistics.  
**Syntax**: `nbtstat -n` or `nbtstat -c`  
**Use**: Troubleshoots NetBIOS name resolution issues.

## Wireless Network Commands

### `netsh wlan show profiles`
**Description**: Displays stored wireless network profiles.  
**Syntax**: `netsh wlan show profiles`  
**Use**: Views saved Wi-Fi networks.

### `netsh wlan show interfaces`
**Description**: Shows wireless adapter information.  
**Syntax**: `netsh wlan show interfaces`  
**Use**: Checks wireless adapter status and connection details.

## Usage Tips

1. Run Command Prompt as Administrator for commands that require elevated privileges
2. Use `/?` after any command to see its help information (e.g., `ipconfig /?`)
3. Combine commands with `>` to redirect output to a file (e.g., `ipconfig /all > network_info.txt`)
4. Use command history with arrow keys for efficiency

## Examples

Basic network info:
```cmd
ipconfig
```

Test connectivity to Google:
```cmd
ping google.com
```

Trace route to a website:
```cmd
tracert example.com
```

View all active connections:
```cmd
netstat -a
```

Check DNS resolution:
```cmd
nslookup microsoft.com
```

This reference covers the most commonly used networking commands in Windows.
