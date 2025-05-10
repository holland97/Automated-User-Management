# Automated-User-Management

This project automates the creation and management of Linux users, groups, packages, and SSH key pairs using Ansible. It is designed to enforce consistency, security, and scalability when managing user access across Linux systems.

📌 Features

✅ Automated Linux user and group creation

🔐 Secure SSH key pair generation per user

🏠 Home directory setup and permission management

📦 System package installation

🔄 Idempotent and repeatable via Ansible playbooks

🔒 Support for Ansible Vault to secure sensitive data

---------------------------------------------------------

🚧 How It Works

- Group Management
Ensures any required groups are present before assigning them to users.

- User Management
Creates users with defined usernames, UIDs, shells, and optional group memberships. Also ensures home directories exist.

- SSH Setup

  - Creates a .ssh directory with secure permissions.

- Uses openssl_privatekey and openssl_publickey to generate Ed25519 key pairs.

- Sets appropriate ownership for each file to the respective user.

- Package Installation
  - Installs additional packages that may be required for user environments.

---------------------------------------------------------

🔐 Security with Ansible Vault

To avoid committing sensitive data (like passwords or keys), this project uses Ansible Vault:
1. Create a vars folder to house a yml file with data that needs to be encrypted

   `` mkdir vars; cd vars; touch setup_ssh.yml ``

2. Encrypt data stored in setup_ssh.yml file

   `` ansible-vault encrypt setup_ssh.yml ``

3. The password used to encrypt setup_ssh.yml can be stored in a .txt file that can be referrence during command execution

   `` ansible-playbook -i inventory/hosts --vault-password-file .vault_pass.txt playbook.yml ``
   
