# Security Infrastructure Design

## Overview
This project presents a **security infrastructure design for a company with approximately 50 employees handling payment data**.  
The objective is to **reduce security risks and protect sensitive financial information** by implementing layered cybersecurity controls across authentication, network infrastructure, endpoint security, and internal policies.

The document proposes a **defense-in-depth strategy** combining encryption, network segmentation, secure authentication, monitoring systems, and security policies.

---

## Objectives

- Protect sensitive **payment and customer data**
- Reduce the risk of **data breaches, ransomware, and unauthorized access**
- Secure both **internal and external network communications**
- Provide safe **remote access for employees**
- Implement **monitoring and incident detection mechanisms**
- Enforce strong **organizational security policies**

---

## Security Architecture

The proposed infrastructure includes several security layers designed to protect systems, users, and data.

### 1. Authentication System

A secure authentication framework is implemented with:

- **Strong password policy**
  - Minimum length requirements
  - Character complexity
  - Dictionary word detection

- **Multi-Factor Authentication (MFA)**
  - Password + additional authentication factors

- **TOTP (Time-Based One-Time Password)**
  - Time-synchronized one-time codes
  - Prevents brute-force attacks even if passwords are compromised

This ensures that only verified users can access internal systems and applications.

---

### 2. Website Security

#### External Website Security

External services use **HTTPS with TLS 1.2 and AES encryption**.

Security benefits include:

- Confidentiality of transmitted data
- Mutual authentication between systems
- Message integrity validation

AES encryption supports key sizes of **128, 192, or 256 bits**, protecting communications from interception and tampering.

This configuration helps prevent **Man-in-the-Middle (MITM) attacks**.

---

#### Internal Website Security

Internal authentication is managed using **LDAP (Lightweight Directory Access Protocol)**.

LDAP acts as a **centralized directory service**, storing user credentials and access information.

To prevent credential interception via packet sniffing:

- **StartTLS encryption** is implemented

This ensures that authentication data is encrypted during transmission.

---

### 3. Secure Remote Access

Remote workers connect through a **VPN using L2TP/IPsec in Tunnel Mode**.

Key security properties:

- **IPsec encryption of IP packets**
- Full packet encapsulation via **Tunnel Mode**
- Protection against interception over public networks

This allows employees to work remotely without exposing internal infrastructure directly to the internet.

---

### 4. Firewall Configuration

The network perimeter is protected with a firewall configured with:

- **Implicit deny policy**
- Only explicitly authorized traffic is permitted

Firewall responsibilities include:

- Packet inspection
- Traffic filtering
- Blocking malicious connections

This helps prevent:

- Malware
- Phishing attempts
- Spam-based attacks

---

### 5. Wireless Network Security

To secure the corporate Wi-Fi network, the infrastructure uses:

**WPA2-Enterprise (802.1X)**

Advantages include:

- Individual authentication per user
- No shared Wi-Fi passwords
- Integration with enterprise authentication systems

This approach reduces the risk of:

- Rogue access points
- Evil twin attacks
- Brute force and dictionary attacks
- Rainbow table attacks

---

### 6. Network Segmentation (VLANs)

The internal network is segmented using **Virtual Local Area Networks (VLANs)**:

| VLAN | Purpose |
|-----|------|
| Employee VLAN | Internal employee devices |
| Guest VLAN | Visitor network access |
| Quarantine VLAN | Isolated network for suspicious devices |

Network segmentation prevents malware or compromised devices from spreading to sensitive systems such as payment servers.

---

### 7. Endpoint Security (Laptops)

Employee devices implement the following protections:

- **Full Disk Encryption (FDE)**
- **Automatic screen lock after 5 minutes of inactivity**

Full Disk Encryption ensures that data remains unreadable without the correct decryption key, protecting against **data theft from lost or stolen devices**.

---

### 8. Application Security Policies

Risky applications are restricted through:

- **Application whitelisting**
- Blocking of:
  - File-sharing software
  - Piracy applications
  - Untrusted software

This approach prevents the execution of unknown or malicious programs.

---

### 9. Security and Privacy Policies

Organizational policies include:

#### Penetration Testing
Regular penetration tests are conducted to identify vulnerabilities in the infrastructure.

#### Principle of Least Privilege (PoLP)

Access to sensitive information is granted only when necessary.

Employees must:

- Request access
- Provide justification
- Specify required data and duration

This minimizes risks caused by **human error or privilege misuse**.

---

### 10. Intrusion Detection and Prevention

To monitor network activity and protect customer databases:

- **IDS (Intrusion Detection System)** monitors network traffic
- **NIPS (Network Intrusion Prevention System)** actively blocks malicious traffic

These systems detect:

- Suspicious traffic patterns
- Unauthorized access attempts
- Potential attacks targeting customer data

---

## Security Benefits

The proposed architecture provides protection against:

- Brute-force attacks
- Man-in-the-middle attacks
- Credential theft
- Malware infections
- Rogue wireless access points
- Unauthorized internal access
- Data exfiltration
- Ransomware attacks

---

## Technologies Used

- HTTPS
- TLS 1.2
- AES Encryption
- LDAP
- StartTLS
- VPN (L2TP/IPsec)
- Firewall with implicit deny
- WPA2-Enterprise (802.1X)
- VLAN segmentation
- Full Disk Encryption
- IDS / NIPS

---

## Conclusion

This security infrastructure design provides a **layered cybersecurity strategy** suitable for a small-to-medium company handling sensitive payment information.

By combining **secure authentication, encrypted communication, network segmentation, monitoring systems, and strict access policies**, the company can significantly reduce the risk of cyberattacks and protect both business and customer data.

---

## Author

Esther López Carretero
