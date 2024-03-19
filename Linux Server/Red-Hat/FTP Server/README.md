# FTP Server Setup Guide

## Overview

FTP (File Transfer Protocol) is a standard network protocol used for transferring files between a client and a server on a computer network. Setting up an FTP server on your Red Hat Linux-based system allows users to upload and download files securely over the network.

## Installation

1. **Update Package Lists:**

    ```bash
    sudo yum update
    ```

2. **Install vsftpd (Very Secure FTP Daemon):**

    ```bash
    sudo yum install vsftpd
    ```

## Configuration

1. **Main Configuration File:**

    The main configuration file for vsftpd is located at `/etc/vsftpd/vsftpd.conf`. This file contains various settings for the FTP server. You can edit it using a text editor like Vim or Nano.

    ```bash
    sudo vim /etc/vsftpd/vsftpd.conf
    ```

    Example Configuration:

    ```conf
    anonymous_enable=NO
    local_enable=YES
    write_enable=YES
    chroot_local_user=YES
    ```

2. **Restart vsftpd Service:**

    After making changes to the configuration file, restart the vsftpd service to apply the changes.

    ```bash
    sudo systemctl restart vsftpd
    ```

## Advanced Configuration Parameters

1. **Anonymous Access:**

    - `anonymous_enable`: Set to `YES` to allow anonymous access or `NO` to disable it.

2. **User Access:**

    - `local_enable`: Set to `YES` to allow local users to log in.
    - `write_enable`: Set to `YES` to enable write permissions for logged-in users.

3. **Directory Restriction:**

    - `chroot_local_user`: Set to `YES` to restrict users to their home directories.

## Usage

1. **Accessing FTP Server:**

    Use an FTP client (such as FileZilla or WinSCP) to connect to the FTP server using its IP address or domain name.

    ```bash
    ftp server_ip
    ```

2. **Logging In:**

    Once connected, you will be prompted to enter your username and password to log in to the FTP server.

3. **Transferring Files:**

    After logging in, you can upload or download files to/from the FTP server using the FTP client.

## Security Considerations

1. **Firewall Configuration:**

    Ensure that the FTP port (default: 21) is open in your firewall to allow FTP connections.

2. **User Authentication:**

    Use strong passwords and consider implementing SSL/TLS encryption for secure authentication.

3. **Monitoring and Logging:**

    Enable logging to monitor FTP access and detect any suspicious activity on the server.

## Conclusion

You have successfully set up and configured an FTP server on your Red Hat Linux-based system. Users can now securely transfer files to and from the server using FTP clients. Ensure to follow security best practices to protect your system from unauthorized access.
