# Day 03 – Create Non-Interactive User & Fix Home Directory (xFusionCorp)

## Task
The system admin team at xFusionCorp Industries required the creation of a user with a
non-interactive shell for a backup agent tool.

## Requirements
- User name: rose
- Server: App Server 3
- Shell: Non-interactive

## Initial Action
The user was initially created using:
```bash
sudo useradd rose

This resulted in:

No home directory being created

Default interactive shell assigned

Issue Identified

The user rose did not have the correct home directory and required a non-interactive shell
as per task requirements.

Fix Applied
Step 1: Set correct home directory
sudo usermod -d /home/rose rose

Step 2: Create home directory
sudo mkdir -p /home/rose

Step 3: Fix ownership
sudo chown -R rose:rose /home/rose

Step 4: Set non-interactive shell
sudo usermod -s /sbin/nologin rose
Verification
bash
Copy code
getent passwd rose
Expected output:

rose:x:UID:GID::/home/rose:/sbin/nologin
Result

User rose was successfully configured with:

Correct home directory

Proper ownership

Non-interactive shell

Real-World Learning

This task reflects real production scenarios where users may be created incorrectly and
require fixes without deleting the account. Using usermod ensures safe updates while
maintaining system stability.