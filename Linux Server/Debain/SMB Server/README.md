# SMB Server Setup Guide

## Overview

SMB (Server Message Block) is a network protocol used for providing shared access to files, printers, and other resources on a network. Setting up an SMB server on your Debian-based system allows you to share files and folders with other devices, including Windows, macOS, and Linux machines.

## Installation

1. **Update Package Lists:**

    ```bash
    sudo apt update
    ```

2. **Install Samba:**

    ```bash
    sudo apt install samba
    ```

## Configuration

1. **Main Configuration File:**

    The main configuration file for Samba is located at `/etc/samba/smb.conf`. This file contains various settings for the SMB server. You can edit it using a text editor like Vim or Nano.

    ```bash
    sudo vim /etc/samba/smb.conf
    ```

    Example Configuration:

    ```conf
    [global]
        workgroup = WORKGROUP
        server string = Samba Server %v
        netbios name = debian
        security = user
        map to guest = bad user
        dns proxy = no

    [share]
        path = /srv/samba/share
        writeable = yes
        guest ok = yes
        guest only = yes
        create mask = 0777
        directory mask = 0777
    ```

2. **Create a Shared Directory:**

    Create a directory that you want to share with other users.

    ```bash
    sudo mkdir -p /srv/samba/share
    ```

3. **Set Permissions:**

    Set appropriate permissions for the shared directory.

    ```bash
    sudo chmod -R 0777 /srv/samba/share
    ```

4. **Restart Samba:**

    After making changes to the configuration file, restart the Samba service to apply the changes.

    ```bash
    sudo systemctl restart smbd
    ```

## Advanced Configuration Parameters

1. **Workgroup:**

    ```conf
    workgroup = WORKGROUP
    ```

2. **Server String:**

    ```conf
    server string = Samba Server %v
    ```

3. **NetBIOS Name:**

    ```conf
    netbios name = debian
    ```

4. **Security Mode:**

    - `user`: User-level security. Requires valid user credentials to access shared resources.
    - `share`: Share-level security. Requires a password for accessing shared resources.

    ```conf
    security = user
    ```

5. **Mapping Guest Users:**

    ```conf
    map to guest = bad user
    ```

6. **DNS Proxy:**

    ```conf
    dns proxy = no
    ```

7. **Share Configuration:**

    - `path`: Path to the shared directory.
    - `writeable`: Specifies if the share is writable.
    - `guest ok`: Allows guest access to the share.
    - `guest only`: Restricts access to only guest users.
    - `create mask`: Sets permissions for newly created files.
    - `directory mask`: Sets permissions for newly created directories.

    ```conf
    [share]
        path = /srv/samba/share
        writeable = yes
        guest ok = yes
        guest only = yes
        create mask = 0777
        directory mask = 0777
    ```

## Usage

1. **Accessing Shared Folder:**

    On Windows:
    
    - Open File Explorer.
    - Enter `\\<samba-server-ip>` in the address bar.
    - Press Enter.

2. **Accessing from Linux:**

    Use a file manager or command-line tools like `smbclient` or `mount.cifs` to access the shared folder.

## Security Considerations

1. **Firewall Configuration:**

    Ensure that the necessary ports (TCP ports 139 and 445) are open in your firewall to allow SMB connections.

2. **User Authentication:**

    Configure user accounts and passwords for accessing shared resources to enhance security.

3. **Encryption:**

    Consider using encryption (such as IPSec or VPN) for securing SMB traffic, especially over untrusted networks.

## Conclusion

You have successfully set up and configured an SMB server on your Debian-based system. You can now share files and folders with other devices on the network using the SMB protocol.
