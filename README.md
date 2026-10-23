# AWS EC2 WireGuard VPN Server

A high-performance, low-latency private VPN server hosted on AWS EC2 using WireGuard. Designed to route encrypted traffic through cloud infrastructure, secure network activity on untrusted Wi-Fi, and bypass regional traffic bottlenecks.

---

## 🛠 Architecture & Features

- **Cloud Provider:** Amazon Web Services (AWS)
- **Compute Instance:** AWS EC2 (`t2.micro` / `t3.micro` - Ubuntu Linux)
- **IP Management:** AWS Elastic IP (EIP) for persistent endpoint addressability
- **VPN Protocol:** WireGuard (UDP)
- **Key Features:**
  - Modern, state-of-the-art cryptography (Noise protocol framework, Curve25519, ChaCha20, Poly1305)
  - Minimal resource footprint and fast handshake establishment
  - Persistent public endpoint via Static Elastic IP
  - Custom Security Group configuration limiting access strictly to WireGuard UDP ports

---

## 📋 Prerequisites

- An active **AWS Account**
- **AWS CLI** installed and configured (optional) or access to the **AWS Management Console**
- A client device running **WireGuard** (Windows, macOS, Linux, iOS, or Android)
- Basic knowledge of Linux shell commands and SSH

---

## 🚀 Deployment & Configuration

### 1. AWS EC2 Provisioning
1. Launch an EC2 Instance using **Ubuntu 22.04 / 24.04 LTS**.
2. Allocate an **Elastic IP (EIP)** in the EC2 Console and associate it with your EC2 instance.
3. Configure the EC2 **Security Group**:
   - **Inbound Rule:** Custom UDP | Port `51820` | Source `0.0.0.0/0`
   - **Inbound Rule:** SSH (TCP) | Port `22` | Source `Your-IP/32` (For administration)

---

### 2. WireGuard Installation & IP Forwarding

1. SSH into your EC2 instance:
   ```bash
   ssh -i your-key.pem ubuntu@<YOUR-ELASTIC-IP>
