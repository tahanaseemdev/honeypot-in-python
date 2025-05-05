# HONEYPY - Multi-Service Honeypot Framework

## Overview
HONEYPY is a Python-based honeypot framework that simulates vulnerable services to detect and log unauthorized access attempts. It currently supports SSH and WordPress admin login simulations.

## Features
- **SSH Honeypot**: Simulates an SSH server with configurable credentials
- **WordPress Honeypot**: Simulates a WordPress admin login page
- **Comprehensive Logging**: Records all access attempts and commands
- **Customizable Credentials**: Set specific usernames/passwords or use defaults
- **Multi-threaded**: Handles multiple concurrent connections

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/honeypy.git
   cd honeypy
   ```

2. Install dependencies:
   ```bash
   pip install paramiko flask
   ```

3. Generate SSH server key (for SSH honeypot):
   ```bash
   ssh-keygen -t rsa -f server.key
   ```

## Usage
```
python honeypy.py -a <IP_ADDRESS> -p <PORT> [OPTIONS]
```

### Options:
- `-a/--address`: IP address to bind to (required)
- `-p/--port`: Port to listen on (required)
- `-u/--username`: Specific username to accept (optional)
- `-pw/--password`: Specific password to accept (optional)
- `-s/--ssh`: Run SSH honeypot
- `-w/--http`: Run WordPress HTTP honeypot

### Examples:
1. Run SSH honeypot on port 2222 with default credentials:
   ```bash
   python honeypy.py -a 0.0.0.0 -p 2222 --ssh
   ```

2. Run WordPress honeypot on port 8080 with custom credentials:
   ```bash
   python honeypy.py -a 0.0.0.0 -p 8080 --http -u admin -pw P@ssw0rd
   ```

## Logging
The honeypot generates detailed logs in the following files:
- `audits.log`: SSH connection attempts
- `cmd_audits.log`: SSH commands executed
- `http_audits.log`: WordPress login attempts

## Customization
- **SSH Honeypot**: Modify `ssh_honeypot.py` to change:
  - Banner (`SSH_BANNER`)
  - Shell responses (`emulated_shell` function)
  - Authentication behavior (`Server` class)

- **WordPress Honeypot**: Modify files in `/templates` to change:
  - Login page appearance
  - Response messages

## Security Considerations
- Only run on isolated systems or protected networks
- Monitor resource usage as attackers may attempt DoS
- Regularly review logs and rotate them as needed

## License
MIT License - See LICENSE file for details

## Contributing
Pull requests and issues are welcome. For major changes, please open an issue first to discuss proposed changes.

## Disclaimer
This tool is for educational and research purposes only. Use responsibly and ensure you have permission to deploy honeypots in your network environment.