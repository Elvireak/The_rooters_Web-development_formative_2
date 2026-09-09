# Web Infrastructure - Client & Server on One Linux Machine

**Module:** Web Infrastructure

**Group:** The Rooters(Group 06)

**Team Members:** Elvire AKAYEZU, Ange Claire UWINEZA, Hildegardine IHIRWE, Lovella TETA NKUSI

**Submission Date:** 06th September 2026

## Overview

This repository contains our group's technical report and supporting files for the "Client & Server on One Linux Machine" assignment. Using a single Ubuntu (WSL2) machine, we set up and tested SSH, NGINX, raw HTTP via Telnet, a public API, and diagnosed a deliberately introduced permissions error, demonstrating that "client" and "server" are roles, not separate physical machines.

## Environment

| Item | Value |
|---|---|
| OS | Ubuntu 20.04.6 LTS (via WSL2 on Windows) |
| Hostname | ANGE-blessing |
| Main user | root |
| Second user | seconduser (created for SSH testing) |
| Loopback IP | 127.0.0.1 |

## What's Covered

### 1. SSH
- Installed and verified `openssh-server`
- Reviewed key settings in `sshd_config` (Port, PasswordAuthentication, PubkeyAuthentication)
- Demonstrated both password login and key-based login (RSA, 4096-bit)
- Transferred files between accounts using both `scp` and an interactive SFTP session

### 2. NGINX & HTTP
- Configured NGINX to serve a custom site from `/var/www/the_rooters`, with a custom `404.html`
- Verified config validity with `nginx -t` and tested with `curl`
- Tested all major HTTP methods (GET, HEAD, POST, PUT, DELETE) and observed their status codes
- Deliberately triggered and documented four status codes: 200, 403, 404, 405
- Added a custom response header (`Group-Name: The_rooters`)

### 3. Telnet
- Used Telnet to confirm NGINX (port 80) and SSH (port 22) were listening
- Stopped/restarted NGINX to prove the port is controlled by the service, not the network itself
- Sent a raw HTTP request manually over Telnet and inspected the response (status line, headers, body)

### 4. Public API Testing
- Used the JSONPlaceholder API (`jsonplaceholder.typicode.com`), here there is no authentication required
- Tested GET, POST, and PUT requests with expected 200/201 responses
- Deliberately triggered a 404 by requesting a non-existent resource, then corrected the request

### 5. Troubleshooting
- **Problem:** Homepage returned 403 Forbidden despite NGINX running correctly
- **Cause:** `chmod 000` had removed all read permissions on `index.html`
- **Fix:** `chmod 644` restored read access, confirmed via `curl` returning 200 again

## Repository Contents

| File | Description |
|---|---|
| `Web_Infrastructure_Report.docx` / `.pdf` | Full technical report with explanations and screenshots |
| `README.md` | This file |

## Repository Link

https://github.com/Elvireak/The_rooters_Web-development_formative_2.git
