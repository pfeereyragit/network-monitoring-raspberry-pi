# network-monitoring-raspberry-pi
Basic network monitoring system using Raspberry Pi and Nagios Core
Network Monitoring System – Raspberry Pi & Nagios
Built a Network Monitoring System using Raspberry Pi and Nagios Core as a learning project.**
Focused on Linux administration, networking, and troubleshooting real dependency and connectivity issues.
Objective:
Monitor network devices (latency, availability and basic traffic)
using a Raspberry Pi and Nagios Core.
Step 1 – Initial Setup
- IP address obtained via Network Manager GUI (Graphical User Interface)
- Initial access via GUI
- Network configuration using Wi-Fi
- Headless access configured via SSH
- Raspberry Pi accessed remotely over Wi-Fi (192.168.1.156)
- IP address assigned dynamically (DHCP – Dynamic Host Configuration Protocol)
Step 2 – System Preparation
- System updated using apt
- SSH access verified from remote host
Step 3 – Network Configuration (Static IP)
Durante esta etapa se intentó configurar una IP estática en la interfaz Wi-Fi utilizando NetworkManager.
El primer intento provocó pérdida de conectividad, por lo que se volvió temporalmente a DHCP desde la GUI.
Posteriormente, la IP estática fue configurada correctamente vía nmcli manteniendo la conectividad por SSH.
Estado final: IP estática configurada y operativa.
Network managed by NetworkManager
Initial static IP configuration caused temporary Wi-Fi connectivity loss
Configuration reverted to DHCP via GUI to restore access
Static IP successfully reconfigured using nmcli over SSH
Wi-Fi connectivity maintained during reconfiguration
Raspberry Pi now uses a static IP (192.168.1.156)
Step 4 – Pre-Installation Checks & System Preparation
Before installing Nagios Core, the system was verified and prepared to ensure
network connectivity and required dependencies were available.
Internet connectivity verified using ICMP (ping)
DNS resolution confirmed
System package index updated using apt
Required build, web server, PHP and SSL dependencies installed
System prepared for Nagios Core compilation and web interface
During dependency installation, package downloads failed due to unreachable mirrors and IPv6 connectivity issues.
The issue was resolved by forcing APT to use IPv4, restoring reliable package downloads.
Step 5 – Nagios Core Installation and Service Initialization
Nagios Core was compiled and installed from source on the Raspberry Pi.
The installation included system integration, Apache web configuration,
and service initialization using systemd.
Nagios Core source code downloaded and extracted
Configuration completed successfully after resolving missing SSL headers
Nagios Core compiled and installed from source
Dedicated Nagios user and command group configured
Apache modules (CGI and rewrite) enabled for Nagios web interface
Web authentication configured using htpasswd
Nagios service started and enabled at boot
Web interface successfully accessed via browser
At this stage, Nagios Core is running correctly.
Local host service checks report alerts due to missing plugins,
which will be addressed in the next step.




Step 6 – Troubleshooting and Resolution
Nagios Core was compiled from source, while monitoring plugins were installed via system packages.
This caused plugin execution failures due to mismatched plugin paths.
The issue was identified through service error messages in the Nagios web interface.
Resolved by aligning plugin execution paths using symbolic links.



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
<img width="1913" height="850" alt="Captura de pantalla 2026-01-07 155147" src="https://github.com/user-attachments/assets/1586a423-8c03-4679-99be-3511a394e8ad" />
<img width="1918" height="867" alt="Captura de pantalla 2026-01-07 154620" src="https://github.com/user-attachments/assets/b98b245a-5602-4fdb-b13d-f238f308bc7e" />
<img width="1891" height="957" alt="Captura de pantalla 2026-01-05 174444" src="https://github.com/user-attachments/assets/6d9e20f2-2d35-4e0c-a37b-e8e6fcb3200f" />
