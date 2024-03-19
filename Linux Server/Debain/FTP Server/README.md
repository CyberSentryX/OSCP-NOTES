# FTP Server Setup Guide

## Overview

FTP (File Transfer Protocol) is a standard network protocol used for transferring files from one host to another over a TCP-based network, such as the internet. Setting up an FTP server on your Debian-based system allows you to securely share files with other users.

## Installation

1. **Update Package Lists:**

    ```bash
    sudo apt update
    ```

2. **Install vsftpd (Very Secure FTP Daemon):**

    ```bash
    sudo apt install vsftpd
    ```

## Configuration

1. **Main Configuration File:**

    The main configuration file for vsftpd is located at `/etc/vsftpd.conf`. This file contains various settings for the FTP server. You can edit it using a text editor like Vim or Nano.

    ```bash
    sudo vim /etc/vsftpd.conf
    ```

    Example Configuration:

    ```conf
    # Disable anonymous FTP access
    anonymous_enable=NO
    
    # Allow local system users to log in
    local_enable=YES
    
    # Enable write access for authenticated users
    write_enable=YES
    
    # Limit each FTP user to their home directory
    chroot_local_user=YES
    ```

2. **User Configuration:**

    By default, vsftpd allows local system users to log in via FTP. You can create additional FTP users and control their access.

    - To create an FTP-only user without shell access:
    
        ```bash
        sudo adduser --home /home/ftpuser --shell /bin/false ftpuser
        ```

3. **Restart vsftpd:**

    After making changes to the configuration file, restart the vsftpd service to apply the changes.

    ```bash
    sudo systemctl restart vsftpd
    ```

## Advanced Configuration Examples

1. **Enabling IPv6:**

    ```conf
    listen=NO
    listen_ipv6=YES
    ```

2. **Restricting User Access to Specific Directories:**

    ```conf
    user_sub_token=$USER
    local_root=/home/$USER/ftp
    ```

3. **Setting Up Virtual Users:**

    Install the `db-util` package:

    ```bash
    sudo apt install db-util
    ```

    Create a new database for virtual users:

    ```bash
    sudo db5.3_load -T -t hash -f /etc/vsftpd/userlist.db /etc/vsftpd/userlist.txt
    ```

    Example `userlist.txt` file:

    ```text
    ftpuser1
    ftpuser2
    ```

    Configure vsftpd to use the virtual user database:

    ```conf
    guest_enable=YES
    guest_username=ftp
    userlist_enable=YES
    userlist_file=/etc/vsftpd/userlist.txt
    userlist_deny=NO
    ```

## Usage

1. **Accessing FTP Server:**

    Use an FTP client (such as FileZilla or WinSCP) to connect to your server using its IP address or domain name, along with the FTP username and password of a valid system user.

2. **Uploading and Downloading Files:**

    Once connected, you can upload files to the server by dragging and dropping them into the FTP client window. Similarly, you can download files from the server to your local machine by selecting them and downloading them.

## Security Considerations

1. **Firewall Configuration:**

    Ensure that the necessary ports (usually TCP ports 20 and 21) are open in your firewall to allow FTP connections.

2. **User Access Control:**

    Control user access by configuring vsftpd to allow or deny certain users or groups from accessing the FTP server.

3. **Encryption:**

    Consider using SSL/TLS encryption for FTP connections to enhance security and protect data in transit.

## Conclusion

You have successfully set up and configured an FTP server on your Debian-based system. You can now securely share files with other users over the network using the FTP protocol.
