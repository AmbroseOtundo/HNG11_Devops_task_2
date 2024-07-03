# HNG11_Devops_task_2
# User Management Script

This Bash script automates the process of creating users, assigning them to groups, and securely managing their passwords on a Linux system.

## Table of Contents
1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [Installation](#installation)
4. [Usage](#usage)
5. [How It Works](#how-it-works)
6. [Log File](#log-file)


## Introduction
This script simplifies the administration of user accounts on a Linux system by automating user creation, group assignment, and secure password management.

## Prerequisites
- **openssl**: Used for encrypting passwords.
- **pwgen**: Used for generating random passwords.
- The script requires **sudo** permissions to perform its operations.

## Installation
Ensure the necessary packages are installed:

```bash
sudo apt-get update
sudo apt-get install openssl pwgen
```

## Usage

### Prepare the Input File
Create a text file (e.g., `users.txt`) containing user data. Each line should follow the format:
```
username;group1,group2,group3
```
Example:
```
user1;group1,group2
user2;group1,group3
```

### Run the Script
1. Make the script executable:
    ```bash
    chmod +x create_users.sh
    ```

2. Execute the script with the path to your user data file as an argument:
    ```bash
    sudo ./create_users.sh /path/to/users.txt
    ```

## How It Works

### Initial Checks
- The script verifies it is run with sudo.
- Redirects output to a log file located at `/var/log/user_management.log`.
- Ensures an input file is provided and exists.

### Dependency Installation
- Checks if `openssl` and `pwgen` are installed, and installs them if necessary.

### User and Group Management
- Reads the input file and processes each line.
- Creates users and assigns them to specified groups.
- Generates and encrypts passwords, storing them securely.

### Password Handling
- Passwords are generated using `pwgen`, encrypted with `openssl`, and stored in `/var/secure/user_passwords.txt`.

## Log File
All actions are logged in `/var/log/user_management.log` for reference and troubleshooting.

