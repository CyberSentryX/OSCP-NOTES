# Debian DHCP Server Setup Guide

## Overview

Dynamic Host Configuration Protocol (DHCP) is a network management protocol used on Internet Protocol (IP) networks for automatically assigning IP addresses and other network configuration parameters to devices. Setting up a DHCP server on your Debian-based Linux machine allows for efficient management of IP address allocation within your network.

## Installation and Configuration

1. **Installation:**

    ```bash
    sudo apt update               # Update package lists
    sudo apt install isc-dhcp-server   # Install DHCP server package
    ```

2. **Configuration:**

    The main configuration file for DHCP server is `/etc/dhcp/dhcpd.conf`. Configure it as needed. Here's an example configuration:

    ```bash
    sudo nano /etc/dhcp/dhcpd.conf
    ```

    Example configuration:

    ```bash
    authoritative;
    subnet 192.168.1.0 netmask 255.255.255.0 {
        range 192.168.1.100 192.168.1.200;
        option routers 192.168.1.1;
        option domain-name-servers 8.8.8.8, 8.8.4.4;
        option subnet-mask 255.255.255.0;
        option broadcast-address 192.168.1.255;
        default-lease-time 600;
        max-lease-time 7200;
    }
    ```

3. **Service Management:**

    ```bash
    sudo systemctl start isc-dhcp-server    # Start DHCP service
    sudo systemctl enable isc-dhcp-server   # Enable DHCP service at startup
    ```

4. **View Assigned IPs:**

    ```bash
    cat /var/lib/dhcp/dhcpd.leases   # View assigned IPs
    ```

## Additional Configuration

- **Exclusion Range:**

    Example:
    ```bash
    subnet 192.168.1.0 netmask 255.255.255.0 {
        range 192.168.1.100 192.168.1.200;
        ...
        deny 192.168.1.150;
        deny 192.168.1.151;
    }
    ```

- **Reserved IP:**

    Example Configuration:
    ```bash
    host pc1 {
        hardware ethernet 00:0C:29:3D:9F:F0;
        fixed-address 192.168.1.10;
    }

    host pc2 {
        hardware ethernet 00:0C:29:3D:9F:F1;
        fixed-address 192.168.1.11;
    }
    ```

- **Deny Unknown Clients:**

    Example:
    ```bash
    subnet 192.168.1.0 netmask 255.255.255.0 {
        ...
        deny unknown-clients;
    }
    ```

## DHCP Server Usage

### Setup
Follow the provided steps to set up the DHCP server on your Debian-based Linux machine.

### Usage
Utilize the configured DHCP server for IP address management on your network.
