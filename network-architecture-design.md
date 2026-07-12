# Network Architecture Design & Security Boundary Review

## 📐 Network Topology & Component Breakdown
![LAN Design Diagram](./lan-diagram.png)

## 📌 Executive Summary
This document outlines the security architecture and structural design of a Local Area Network (LAN) engineered to protect internal corporate assets from external network threats. The design implements strict perimeter defenses and internal segmentation to enforce defense-in-depth principles.

---

## 🔍 Component Breakdown & Security Objectives

### 1. Boundary Defense (Firewall)
*   **Placement:** Deployed at the immediate perimeter between the public internet and the internal router.
*   **Security Objective:** Acts as the primary line of defense to filter inbound and outbound traffic based on defined security rulesets (ACLs), blocking unauthorized access attempts before they hit the internal network.

### 2. Network Routing (Router)
*   **Placement:** Positioned immediately behind the primary firewall.
*   **Security Objective:** Directs traffic dynamically between different internal subnets and manages external data traffic heading toward the public internet gateway.

### 3. Local Segmentation (Switches)
*   **Placement:** Deployed within internal segments behind the router.
*   **Security Objective:** Facilitates fast, localized communication between end-user workstations and internal servers, ensuring that broadcast domains are contained and network sniffing risks are minimized.

---

## 🔄 Network Model Reference (TCP/IP Framework)
To properly analyze future data packages (e.g., using `tcpdump` or `Wireshark`), this architecture aligns with the **TCP/IP Model Layers**:

*   **Application Layer:** Where user protocols (HTTPS, SSH, SFTP) interact with software applications.
*   **Transport Layer:** Where data flow controls are managed using **TCP** (connection-oriented, guaranteed delivery) or **UDP** (connectionless, rapid streaming).
*   **Internet Layer:** Where logical routing takes place using IP addressing schemes.
*   **Network Access Layer:** Where physical hardware media and MAC address delivery occur on the local switches.

---

## 🔒 Security Hardening & Implementation Controls

To transition this basic architecture into a secure enterprise environment, the following defensive controls should be implemented based on the Google Cybersecurity framework:

### 1. Network Segmentation (VLANs)
*   **Implementation:** Divide the flat network into distinct Virtual Local Area Networks (VLANs) to separate sensitive business units (e.g., separating HR and Finance from general guest Wi-Fi).
*   **Security Impact:** Limits lateral movement. If an attacker compromises a device on the guest network, they cannot easily pivot to critical company databases.

### 2. Firewall Access Control Lists (ACLs)
*   **Implementation:** Deploy a Next-Generation Firewall (NGFW) at the edge router to drop unauthorized inbound traffic.
*   **Security Rule Example:** 
    *   *Allow* inbound traffic on Ports 80/443 (HTTP/HTTPS) only to the public web server.
    *   *Deny* all inbound SSH (Port 22) and RDP (Port 3389) requests from the public internet.

### 3. Monitoring & Intrusions Detection (IDS/IPS)
*   **Implementation:** Configure an open-source IDS tool like **Suricata** or **Snort** at the main switch mirroring port to analyze packet headers and payloads.
*   **Security Impact:** Provides real-time alerts if signature-based malicious activity or network scanning is detected.
