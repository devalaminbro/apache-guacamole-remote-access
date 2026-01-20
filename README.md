# 🌐 Apache Guacamole - Clientless Remote Access Gateway

![Container](https://img.shields.io/badge/Docker-Compose-blue)
![App](https://img.shields.io/badge/App-Apache%20Guacamole-red)
![Access](https://img.shields.io/badge/Access-RDP%20%7C%20SSH%20%7C%20VNC-green)

## 📖 Overview
System Administrators often need to access critical servers while traveling or from devices where installing VPN clients or SSH tools (Putty/WinSCP) is restricted.

This repository provides a **Production-Ready Docker Setup** for **Apache Guacamole**. It acts as a centralized gateway that allows you to access your entire infrastructure (Windows RDP, Linux SSH, VNC) directly from any **HTML5 Web Browser** (Chrome, Firefox, Safari).

## 🛠 Features
- 🌍 **Clientless Access:** No plugins or software required on the client side.
- 🔐 **Centralized Security:** Supports 2FA (TOTP) and LDAP/Active Directory authentication.
- 📹 **Session Recording:** Automatically records SSH/RDP sessions for auditing purposes.
- 📋 **Clipboard Sync:** Copy-paste text seamlessly between your local machine and the remote server.

## ⚙️ Architecture
- **Guacd:** The proxy daemon that translates RDP/SSH protocols.
- **Guacamole Client:** The Tomcat-based web frontend.
- **PostgreSQL:** Stores connection profiles and user data.

## 🚀 Deployment Guide

### 1. Prerequisites
- A Linux Server with Docker & Docker Compose installed.
- Public IP or Domain pointed to the server.

### 2. Installation
Clone the repository and start the stack:
```bash
git clone [https://github.com/devalaminbro/apache-guacamole-remote-access.git](https://github.com/devalaminbro/apache-guacamole-remote-access.git)
cd apache-guacamole-remote-access
docker-compose up -d

3. Initialization (First Run Only)
You need to initialize the database schema:
docker run --rm guacamole/guacamole /opt/guacamole/bin/initdb.sh --postgres > initdb.sql
cat initdb.sql | docker exec -i guac_postgres psql -U guacamole_user -d guacamole_db

4. Access the Dashboard
Open your browser: http://your-server-ip:8080/guacamole/

Default User: guacadmin

Default Pass: guacadmin

(Change the password immediately after login)

⚠️ Security Note
For production use, it is highly recommended to run this behind an Nginx Reverse Proxy with SSL (Let's Encrypt) enabled.

Author: Sheikh Alamin Santo
Cloud Infrastructure Specialist & DevOps Engineer
