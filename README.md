
# 🐧 Linux System Administration & Troubleshooting

## Project Overview

This repository documents hands-on Linux system administration and troubleshooting exercises using Ubuntu Linux.

The project focuses on user and group administration, file permissions, process management, system monitoring, and network diagnostics.

**Environment:** Ubuntu Linux  
**Interface:** Linux Terminal (Bash)  
**Project Type:** Hands-on Technical Lab  
**Status:** Documentation and verification in progress

## Objectives

- Administer Linux users and groups.
- Configure file permissions and ownership.
- Monitor system performance and resource usage.
- Manage Linux processes and services.
- Diagnose network connectivity issues.
- Document troubleshooting procedures and results.

## 1. User and Group Administration

### Commands

```bash
sudo adduser labuser
sudo groupadd itsupport
sudo usermod -aG itsupport labuser
id labuser
groups labuser
```

### Explanation

These commands create a test user, create an IT support group, assign the user to that group, and verify group membership.

### Verification

Record the output of:

```bash
id labuser
```

## 2. File Permissions and Ownership

### Commands

```bash
mkdir -p ~/linux-lab
touch ~/linux-lab/testfile.txt
chmod 640 ~/linux-lab/testfile.txt
ls -l ~/linux-lab/testfile.txt
```

### Explanation

The `640` permission setting gives the file owner read/write access, the group read-only access, and others no access.

## 3. System Monitoring

### Commands

```bash
uptime
free -h
df -h
top
```

### Explanation

These commands display system uptime, memory usage, disk utilization, and running processes.

## 4. Service Management

### Commands

```bash
systemctl --failed
systemctl list-units --type=service --state=running
journalctl -p err -n 20 --no-pager
```

### Explanation

These commands help identify failed services, review running services, and investigate recent system errors.

## 5. Network Troubleshooting

### Commands

```bash
ip addr
ip route
ping -c 4 1.1.1.1
getent hosts github.com
ss -tuln
```

### Explanation

These commands help inspect network interfaces, routing, IP connectivity, DNS resolution, and listening ports.

## Evidence and Results

Add sanitized screenshots and command outputs after completing the exercises.

For each exercise, document:

1. The administrative or troubleshooting objective.
2. Commands executed.
3. Relevant output.
4. Findings and any corrective action.
5. Verification of the final result.

## Security Considerations

All exercises should be performed in an authorized lab environment. Do not upload passwords, private keys, access tokens, or confidential system information.

## Author

**Anointing Ibeh**  
IT Support | Cybersecurity | Linux Administration

GitHub: https://github.com/AnoinTech


## Documented Projects

### AWS EC2 Linux Administration & SSH Troubleshooting

Hands-on Linux administration lab involving remote Ubuntu server access, SSH authentication troubleshooting, and secure private-key file permissions.

**Technologies:** Ubuntu Linux, AWS EC2, OpenSSH, Bash

[View AWS EC2 Lab](./aws-ec2-ssh-troubleshooting/README.md)


## Featured Hands-On Project

### AWS EC2 Linux Administration & SSH Troubleshooting

Configured and accessed an Ubuntu Linux instance hosted on AWS EC2.

Diagnosed an SSH authentication failure caused by overly permissive private-key file permissions.

Corrected the issue using `chmod 400` and successfully established a secure SSH connection.

**Technologies:** AWS EC2, Ubuntu Linux, SSH, Bash

 [View Project Documentation](./aws-ec2-ssh-troubleshooting/README.md)


