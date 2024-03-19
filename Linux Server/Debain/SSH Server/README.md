# SSH Server Setup Guide

## Overview

SSH (Secure Shell) is a network protocol that allows secure remote access to a computer or server. Setting up an SSH server on your Debian-based system enables users to securely connect to the server and execute commands remotely.

## Installation

1. **Update Package Lists:**

    ```bash
    sudo apt update
    ```

2. **Install OpenSSH Server:**

    ```bash
    sudo apt install openssh-server
    ```

## Configuration

1. **Main Configuration File:**

    The main configuration file for SSH server is located at `/etc/ssh/sshd_config`. This file contains various settings for the SSH service. You can edit it using a text editor like Vim or Nano.

    ```bash
    sudo vim /etc/ssh/sshd_config
    ```

    Example Configuration:

    ```conf
    # Port to listen on
    Port 22
    
    # Permit root login
    PermitRootLogin no
    
    # Allow only specific users to login
    AllowUsers username1 username2
    
    # Disable password authentication
    PasswordAuthentication no
    ```

2. **Restart SSH Service:**

    After making changes to the configuration file, restart the SSH service to apply the changes.

    ```bash
    sudo systemctl restart sshd
    ```

## Advanced Configuration Parameters

1. **Changing SSH Port:**

    To change the default SSH port (22), modify the `Port` directive in the configuration file.

    ```conf
    Port 2222
    ```

2. **Allowing Root Login:**

    To permit root login, set `PermitRootLogin` to `yes`.

    ```conf
    PermitRootLogin yes
    ```

3. **Allowing Specific Users:**

    To allow only specific users to log in, use the `AllowUsers` directive followed by the usernames separated by spaces.

    ```conf
    AllowUsers user1 user2
    ```

4. **Disabling Password Authentication:**

    To disable password authentication and enforce the use of SSH keys, set `PasswordAuthentication` to `no`.

    ```conf
    PasswordAuthentication no
    ```

## Usage

1. **Accessing SSH Server:**

    Use an SSH client (such as OpenSSH, PuTTY, or WinSCP) to connect to the SSH server using its IP address or domain name.

    ```bash
    ssh username@server_ip
    ```

2. **Logging In:**

    Once connected, you will be prompted to enter the password for the specified user. If SSH keys are configured, you may be prompted for the passphrase instead.

3. **Executing Commands:**

    After logging in, you can execute commands on the remote server as if you were physically present on the system.

## Security Considerations

1. **Firewall Configuration:**

    Ensure that the SSH port (default: 22) is open in your firewall to allow SSH connections.

2. **SSH Key Authentication:**

    Use SSH keys for authentication instead of passwords to enhance security and prevent brute-force attacks.

3. **Limiting Access:**

    Restrict SSH access to specific users and IP addresses to minimize the attack surface.

## Conclusion

You have successfully set up and configured an SSH server on your Debian-based system. Users can now securely connect to the server and execute commands remotely using SSH. Ensure to follow security best practices to protect your system from unauthorized access.
