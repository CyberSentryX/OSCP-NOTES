# SMB Server Setup Guide

## Overview

SMB (Server Message Block) is a network file sharing protocol commonly used in Windows environments. Setting up an SMB server on your Red Hat Linux system allows you to share files and resources with other devices on the network.

## Installation

1. **Update Package Lists:**

    ```bash
    sudo yum update
    ```

2. **Install Samba Server:**

    ```bash
    sudo yum install samba
    ```

## Configuration

1. **Configure Samba Share:**

    Edit the Samba configuration file `/etc/samba/smb.conf` to define the shares you want to create.

    ```bash
    sudo vim /etc/samba/smb.conf
    ```

    Example Configuration:

    ```conf
    [shared_folder]
        path = /path/to/shared/folder
        valid users = @smbgroup
        writable = yes
        browseable = yes
    ```

    - `[shared_folder]`: Name of the shared folder.
    - `path`: Path to the folder you want to share.
    - `valid users`: List of users allowed to access the share.
    - `writable`: Specifies whether users can write to the share.
    - `browseable`: Specifies whether the share is visible in network browsing.

2. **Create Samba User:**

    Create a Samba user and set a password to access the shares.

    ```bash
    sudo smbpasswd -a username
    ```

3. **Restart Samba Service:**

    After making changes to the configuration file, restart the Samba service to apply the changes.

    ```bash
    sudo systemctl restart smb
    ```

## Usage

1. **Accessing Shared Folder from Windows:**

    Open File Explorer on a Windows machine and navigate to `\\<Linux_Server_IP>\shared_folder`. You will be prompted to enter the username and password of the Samba user.

2. **Accessing Shared Folder from Linux:**

    Use the `smbclient` command to access the shared folder from a Linux machine.

    ```bash
    smbclient //Linux_Server_IP/shared_folder -U username
    ```

3. **Mounting Shared Folder:**

    You can mount the shared folder on a Linux machine using the `mount` command or by adding an entry to `/etc/fstab`.

    ```bash
    sudo mount -t cifs //Linux_Server_IP/shared_folder /mnt/shared_folder -o username=username,password=password
    ```

## Security Considerations

1. **Firewall Configuration:**

    Allow Samba traffic (TCP ports 137-139, 445) through the firewall.

    ```bash
    sudo firewall-cmd --permanent --add-service=samba
    sudo firewall-cmd --reload
    ```

2. **Limit Access:**

    Restrict access to the shares by specifying valid users in the Samba configuration.

3. **Encryption:**

    Enable SMB encryption to secure data transmission over the network.

    ```bash
    server min protocol = SMB2
    server max protocol = SMB3
    ```

## Conclusion

You have successfully set up an SMB server on your Red Hat Linux system, allowing users to share files and resources across the network. Ensure to follow security best practices to protect the shared data from unauthorized access.
