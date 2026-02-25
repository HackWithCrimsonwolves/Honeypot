# Honeypot

**Honeypot** is a Python-based honeypot system designed to simulate real-world attack surfaces and capture malicious activity.

It includes:
- SSH Honeypot (fake SSH server)
- Web Honeypot (fake WordPress login page)

# 🛡️ Features

- Simulates real-world attack surfaces using both SSH and a WordPress-style login interface
- Captures attacker credentials including usernames, passwords, and source IP addresses
- Provides a fake interactive shell environment to observe post-login attacker behavior safely
- Logs all activities such as login attempts and executed commands for analysis
- Supports modular execution through a single controller script using command-line arguments
- Uses multithreading and rotating logs to handle multiple connections efficiently without data loss

# 🧪 Installation

**1) Clone repository**
```
https://github.com/HackWithCrimsonwolves/Honeypot.git
```

**2) Create Virtual Environment**
```
python3 -m venv .venv
```
```
source .venv/bin/activate
```

**3) Install Dependencies**
```
pip install paramiko
```
```
pip install flask
```

**4) Generate SSH Host Key**

An RSA key must be generated for the SSH server host key. The SSH host key provides proper identification for the SSH server. Ensure the key is titled `server.key` and resides in the same relative directory to the main program.
```
ssh-keygen -t rsa -b 2048 -f server.key
```

# 🚀 Usage

To provision a new instance of HONEYPOT, use the `honeypy.py` file. This is the main file to interface with for HONEYPOT. 

HONEYPOT requires a bind IP address (`-a`) and network port to listen on (`-p`). Use `127.0.0.1` to listen on all network interfaces. The protocol type must also be defined.

```
-a / --address: Bind address
-p / --port: Port
-s / --ssh OR --http: Declare honeypot type
```

Example: `python3 honeypy.py -a 127.0.0.1 -p 2223 --ssh`


**Optional Arguments**

A username (`-u`) and password (`-w`) can be specified to authenticate the SSH server. The default configuration will accept all usernames and passwords.

```
-u / --username: Username
-w / --password: Password
```

Example: `python3 honey.py -a 127.0.0.1 -p 2223 -u admin -pw password --ssh`

# 📁 Logging Files

HONEYPOT has three loggers configured. Loggers will route to either `cmd_audits.log`, `creds_audits.log` (for SSH), and `http_audit.log` (for HTTP) log files for information capture.

`cmd_audits.log`: Captures IP address, username, password, and all commands supplied.

`creds_audits.log`: Captures IP address, username, and password, comma seperated. Used to see how many hosts attempt to connect to SSH_HONEYPY.

`http_audit.log`: Captures IP address, username, password.

# 📊 Honeypot Types
This honeypot was written with modularity in mind to support future honeypot types (Telnet, HTTPS, SMTP, etc). As of right now there are two honeypot types supported.

## SSH
The project started out with only supported SSH. Use the following instructions above to provision an SSH-based honeypot which emulates a basic shell.

## HTTP
Using Python Flask as a basic template to provision a simple web service, HONEYPOT impersonates a default WordPress `wp-admin` login page. Username / password pairs are collected.

The web-based honeypot runs on port 5000 by default.

## 🔐 Use Case

Can be deployed on:

- VPS
- Cloud instances
- Lab environments

to monitor real-world attack attempts.

## ⚠️ Disclaimer

This project is for:

Educational & defensive security research purposes only.

## 🤝 Contributing

Pull requests and suggestions are welcome!

---
Made with ❤️ by Aditya Jain
