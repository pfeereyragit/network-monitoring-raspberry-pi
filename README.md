             Network Monitoring System: Raspberry Pi & Nagios Core


This project involves the implementation of a robust Network Monitoring System using a Raspberry Pi and Nagios Core. It was designed as a learning project to master Linux administration, networking, and real-world troubleshooting of dependencies and connectivity.


🎯 Objectives
• Active Monitoring: Supervise network devices for latency, availability, and basic traffic metrics.
• Infrastructure: Deploy a dedicated monitoring server on low-cost hardware (Raspberry Pi).
• Service Management: Configure an automated environment that ensures high availability of the monitoring service itself.
🛠️ Tech Stack & Skills
• OS: Linux (Debian-based/Raspberry Pi OS).
• Monitoring Tool: Nagios Core (Compiled from source).
• Web Server: Apache (CGI, rewrite modules).
• Networking: Static IP configuration, SSH, ICMP, DNS resolution, DHCP,.
• Security/Admin: htpasswd authentication, systemd service management, and nmcli,.
🚀 Implementation Highlights
1. Network & Access Optimization
The project transitioned from a standard GUI-based DHCP setup to a professional headless configuration.
• Challenge: An initial attempt to set a static IP via the Network Manager GUI caused a total loss of connectivity.
• Solution: Reverted to DHCP to restore access, then successfully utilized the nmcli command-line tool to configure the static IP (192.168.1.156) while maintaining an active SSH session,.
2. System Hardening & Dependency Management
Before installation, the environment was audited for reliability:
• Connectivity Verification: Confirmed internet access and DNS resolution via ICMP (ping).
• Advanced Troubleshooting: Resolved package download failures caused by unreachable mirrors and IPv6 issues by forcing APT to utilize IPv4, ensuring a stable dependency installation.
3. Source-Code Installation of Nagios Core
To gain a deeper understanding of system integration, Nagios Core was compiled and installed from source rather than using a package manager.
• Configuration: Created dedicated Nagios users/groups and configured Apache with web authentication via htpasswd.
• Persistence: Integrated the service with systemd to ensure Nagios starts automatically at boot,.
🔍 Troubleshooting (The "Portfolio" Highlight)
A critical part of this project was resolving service-level errors post-installation:
• The Issue: Nagios reported "CRITICAL" alerts for local services because monitoring plugins (installed via system packages) were not in the directory expected by the source-compiled Nagios Core.
• The Resolution: Identified the path mismatch through service error messages in the web interface and resolved it by aligning plugin execution paths using symbolic links. This transitioned all monitored services from "CRITICAL" to "OK",.
📊 Monitoring Scope
Feature
Description
ICMP Connectivity
Ping monitoring for device availability.
HTTP Service
Monitoring availability of web services.
Disk Usage
Local system health and storage alerts.
External Connectivity
Testing outbound access (Ping to Google DNS).
🖼️ Evidence of Work
The system is fully operational, as evidenced by the Nagios dashboard showing active services and the systemctl status confirming the service is active and enabled,.

--------------------------------------------------------------------------------
Portfolio Note: This project demonstrates my ability to handle end-to-end system deployments, from physical hardware configuration to solving complex path-dependency issues in a Linux environment.




Monitoring Scope
Implemented monitoring checks focused on availability and basic system health:
ICMP connectivity (Ping)
HTTP service availability
Disk usage monitoring
External connectivity test (Ping to Google DNS)
Out-of-scope:
Advanced performance tuning
Full traffic analysis
Enterprise-scale monitoring
SIEM or intrusion detection




Skills Demonstrated
Linux system administration (Debian-based)
SSH remote administration
Network configuration (DHCP / Static IP)
Service installation and management (systemd)
Web server configuration (Apache)
Monitoring concepts and alerting
Troubleshooting dependency and path issues
Documentation and project scoping

Nagios web interface showing service status##
<img width="1912" height="1012" alt="Nagios Web Interface" src="https://github.com/user-attachments/assets/daee62d9-a6c0-4109-82b2-23d1887392ef" />
Services transitioning from CRITICAL to OK (initial plugin path mismatch) Before##
<img width="1913" height="850" alt="Captura de pantalla 2026-01-07 155147" src="https://github.com/user-attachments/assets/1586a423-8c03-4679-99be-3511a394e8ad" />
after##
<img width="1918" height="867" alt="Captura de pantalla 2026-01-07 154620" src="https://github.com/user-attachments/assets/b98b245a-5602-4fdb-b13d-f238f308bc7e" />

- Nagios service running and enabled at boot (`systemctl status nagios`##
<img width="1891" height="957" alt="Captura de pantalla 2026-01-05 174444" src="https://github.com/user-attachments/assets/6d9e20f2-2d35-4e0c-a37b-e8e6fcb3200f" />
