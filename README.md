# EC2-S3-Attack 

# Cloud Security Vulnerability Test and Hardening Project

## Overview

This project demonstrates a hands-on cloud security assessment and remediation using AWS services. It includes:

- Setting up an **AWS EC2 instance** and an **S3 bucket** with intentional misconfigurations.
- Simulating an attack by exploiting a **publicly accessible S3 bucket** and an open **EC2 SSH port**.
- Performing basic post-exploitation actions to understand the attack surface.
- Implementing **Blue Team defenses** to secure the environment and mitigate risks.

---

## Project Components

### 1. Vulnerability Setup (Red Team Phase)

- Created an **S3 bucket with public read access**.
- Uploaded a **dummy sensitive file** to the S3 bucket.
- Launched an **EC2 instance** with open SSH access (`0.0.0.0/0`).
- Demonstrated access to the sensitive file via public URL.
- Demonstrated SSH access and scanning possibilities on EC2.

### 2. Defense and Hardening (Blue Team Phase)

- **Made the S3 bucket private** by enabling "Block all public access" and removing open bucket policies.
- **Restricted EC2 SSH access** to only my personal IP address via Security Group inbound rules.
- **Rotated EC2 key pairs** by terminating the vulnerable instance and launching a new instance with a new key pair.
- Installed and enabled **UFW firewall** on the EC2 instance to restrict unauthorized access.
- (Optional) Created and attached an **IAM role with least privilege** policy for EC2 access to S3.

---

## Tools and Technologies Used

- AWS EC2 and S3
- AWS IAM for access control
- Linux terminal with `ssh`, `curl`, and AWS CLI
- UFW firewall on Ubuntu EC2
- Basic scripting for file creation and upload

---

## Screenshots

Screenshots of each step are included below. Sensitive information such as IP addresses and personal usernames have been blurred to protect privacy.

---

## Lessons Learned

- Understanding how misconfigured cloud resources can lead to data exposure.
- Practical experience with AWS Security Groups, IAM policies, and key management.
- Importance of network restrictions and firewall configurations.
- Value of rotating credentials post-incident.
- Basic Linux security tools installation and usage.

---

## Future Work

- Implement automated monitoring and alerts (e.g., AWS GuardDuty).
- Explore more advanced IAM policies and roles.
- Set up logging and audit trails for compliance.

---

EC2 instance created - Launched a vulnerable EC2 instance using a public key and open SSH access from all IPs (0.0.0.0/0).

<img width="1417" alt="ec2-instance-created" src="https://github.com/user-attachments/assets/1ccad811-6ddf-41a1-8bf0-d7cec55d9342" />

Created S3 Bucket - Created an S3 bucket with misconfigured public access to simulate a real-world data exposure scenario.

<img width="1417" alt="created-s3" src="https://github.com/user-attachments/assets/37a78234-b2b7-4901-aef0-98ac3280a8d4" />

Created a sensitive file -- Generated a dummy "sensitive" file (e.g., password.txt) to demonstrate potential data leakage if exposed.

<img width="566" alt="Edit-Secret-data" src="https://github.com/user-attachments/assets/ba1975d3-dbdf-4c77-ab60-3236e7896a10" />

Uploaded the fake sensitive file to the S3 bucket while public access was still enabled.

<img width="1318" alt="Upload-sens-complete" src="https://github.com/user-attachments/assets/f7f30681-fc89-4e91-906d-4d4c6748d6fa" />

Demonstrated unauthorized access to the file using a simple curl command without authentication.

<img width="565" alt="hacked-sensitive-data" src="https://github.com/user-attachments/assets/e3d9a59c-5fc2-4c81-9497-d1340aaae1e8" />

Hardened the EC2 instance by modifying the security group to allow SSH only from my IP.

<img width="1410" alt="new-ec2-rules" src="https://github.com/user-attachments/assets/9582a594-7c3b-45be-80db-41cb481de83b" />

Now Blocking ALL public access

<img width="1126" alt="Screenshot 2025-07-02 at 5 49 10 PM" src="https://github.com/user-attachments/assets/5bf87922-5364-4953-abcc-6e18cf1b5f6a" />

Simulated credential rotation by terminating the original instance and launching a new EC2 with a fresh key pair.
<img width="1410" alt="new created key pair" src="https://github.com/user-attachments/assets/8df0e3e8-977e-490a-8857-137da437d2bd" />

Status - Installed and enabled UFW firewall on EC2, allowing only SSH connections for further internal hardening.

<img width="559" alt="ufw status" src="https://github.com/user-attachments/assets/3b752390-32c7-4715-9199-88e0d19c4329" />

