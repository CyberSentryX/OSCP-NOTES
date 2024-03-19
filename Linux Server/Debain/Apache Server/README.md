# Apache Server Setup Guide

This guide provides step-by-step instructions for setting up an Apache web server on Debian, including PHP and MySQL configurations, along with binding multiple sites and installing WordPress.

## Prerequisites

Before starting, ensure you have administrative privileges and a Debian-based system.

```bash
$ apt update && apt upgrade
$ apt install vim fonts-lato fonts-open-sans fonts-roboto fonts-mononoki fonts-indic grc gcc-multilib g++-multilib libtesseract-dev jq testssl.sh zsh libpcab-dev build-essential libssl-dev libffi-dev python-dev net-tools curl wget unzip


# Apache Installation
Install Apache and PHP along with necessary modules:

```bash
$ apt install apache2 php php7.4 php7.4-common php7.4-mbstring php7.4-xmlrpc php7.4-soap php7.4-gd php7.4-xml php7.4-intl php7.4-mysql php7.4-cli php7.4-ldap php7.4-zip php7.4-curl php-xml composer composer

