# Honeypot

**Honeypot** is a Python-based honeypot system designed to simulate real-world attack surfaces and capture malicious activity.

It includes:
SSH Honeypot (fake SSH server)
Web Honeypot (fake WordPress login page)

# Features

- Simulates real-world attack surfaces using both SSH and a WordPress-style login interface
- Captures attacker credentials including usernames, passwords, and source IP addresses
- Provides a fake interactive shell environment to observe post-login attacker behavior safely
- Logs all activities such as login attempts and executed commands for analysis
- Supports modular execution through a single controller script using command-line arguments
- Uses multithreading and rotating logs to handle multiple connections efficiently without data loss

# Installation

**1) Clone repository**
`
https://github.com/HackWithCrimsonwolves/Honeypot.git
`
**2) Create Virtual Environment**
`
python3 -m venv .venv
`
`
source .venv/bin/activate
`
**3) Install Dependencies**
`
pip install paramiko
`
`
pip install paramiko
`
**4) Generate SSH Host Key**
An RSA key must be generated for the SSH server host key. The SSH host key provides proper identification for the SSH server. Ensure the key is titled `server.key` and resides in the same relative directory to the main program.
`
ssh-keygen -t rsa -b 2048 -f server.key
`
