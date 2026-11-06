# AWS EC2 Linux Server Administration and SSH Troubleshooting

**Portfolio:** AnoinTech  
**Focus:** Linux administration · AWS EC2 · SSH · troubleshooting

## Project overview

This lab documents remote access to an Ubuntu 24.04 LTS Linux instance hosted on Amazon EC2. The screenshots capture a real SSH authentication problem caused by overly permissive private-key file permissions, the corrective action, and a successful remote login.

> **Evidence note:** This repository reconstructs the documented workflow from screenshots of a previously completed lab. Original infrastructure and full command history are not available. It does not claim a reproducible deployment or configuration steps not shown in the evidence.

## Technologies

- Amazon Web Services (AWS) EC2
- Ubuntu 24.04 LTS
- OpenSSH client and key-based authentication
- Linux terminal and filesystem permissions

## Lab workflow and troubleshooting

1. **Attempted SSH access.** The first attempt returned `Permissions 0755 for 'ops345.pem' are too open` and `Permission denied (publickey)`. SSH refused to use the private key because other users could access it.
2. **Located the correct key.** The terminal output shows an initial attempt to change permissions on `ops345` (without the `.pem` extension), which failed because that filename did not exist. A directory listing then showed `ops345.pem`.
3. **Corrected private-key permissions.** The following command was run from the directory containing the key:

   ```bash
   chmod 400 ops345.pem
   ```

   Mode `400` grants read permission to the file owner only.
4. **Retried SSH authentication.** The terminal shows a successful SSH session using the key:

   ```bash
   ssh -i "ops345.pem" ubuntu@<EC2_PUBLIC_IP>
   ```

5. **Verified the remote session.** On the Ubuntu instance, `pwd` returned `/home/ubuntu`, confirming that the command was executed within the remote user's home directory.

## Screenshot evidence

### 1. Ubuntu instance terminal

![Ubuntu EC2 terminal showing OS information and pwd](screenshots/01-aws-ec2-ubuntu-terminal.png)

The AWS console terminal shows Ubuntu 24.04.3 LTS and a shell prompt on the instance, followed by `pwd` returning `/home/ubuntu`.

### 2. SSH troubleshooting and successful connection

![SSH private key permission correction followed by successful Ubuntu login](screenshots/02-ssh-key-permissions-and-successful-login.png)

The local terminal captures the private-key permission error, correction using `chmod 400`, successful SSH login, and verification using `pwd`.

## Results

- Identified the cause of a failed SSH public-key authentication attempt.
- Corrected a Linux private-key file permission issue.
- Established an authenticated SSH session with an Ubuntu EC2 instance.
- Verified remote shell access with a basic Linux command.

## Skills demonstrated

Linux command-line troubleshooting, file permission management, SSH key-based authentication, remote server access, and interpreting terminal error messages.

## Security and scope

- Private key files (`*.pem`) and passwords are **not included** in this repository.
- Account identifiers and public connection details have been obscured in the portfolio screenshots.
- The screenshots substantiate access and troubleshooting; they do not independently verify EC2 provisioning, IAM setup, security group rules, or production hardening.

## Repository maintenance

Documentation based on historical lab evidence. The original EC2 instance may no longer be available.
