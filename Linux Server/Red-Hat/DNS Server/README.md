# DNS Server Setup Guide

## Overview

A DNS (Domain Name System) server is responsible for translating domain names into IP addresses and vice versa. Setting up a DNS server on your Red Hat Linux-based system allows you to host your own DNS records and manage domain name resolution for your network.

## Installation

1. **Update Package Lists:**

    ```bash
    sudo yum update
    ```

2. **Install BIND (Berkeley Internet Name Domain):**

    ```bash
    sudo yum install bind bind-utils
    ```

## Configuration

1. **Main Configuration File:**

    The main configuration file for BIND is located at `/etc/named.conf`. This file contains various settings for the DNS server. You can edit it using a text editor like Vim or Nano.

    ```bash
    sudo vim /etc/named.conf
    ```

    Example Configuration:

    ```conf
    include "/etc/named.rfc1912.zones";
    include "/etc/named.root.key";
    ```

2. **Zone Configuration:**

    Edit zone files to define domains hosted by the DNS server.

    ```
