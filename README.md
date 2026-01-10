             Network Monitoring System: Raspberry Pi & Nagios Core


This project involves the implementation of a robust Network Monitoring System using a Raspberry Pi and Nagios Core. It was designed as a learning project to master Linux administration, networking, and real-world troubleshooting of dependencies and connectivity.
Raspberry Pi and Nagios: System State Monitoring and Control

This documentation details the implementation of a network monitoring system using a Raspberry Pi and Nagios Core software. The process covers everything from initial hardware setup and assigning a static IP address, to preparing the Linux environment with dependencies such as Apache, PHP, and SSL.
It describes the resolution of critical issues, such as IPv6 connectivity errors and fixing execution paths using symbolic links so that plugins would work correctly.
The project demonstrates skills in server administration and monitoring essential services such as latency and disk status. This technical guide serves as evidence of a complete workflow that combines source code installation, network management, and system troubleshooting.

Initial Configuration and Remote Access

Hardware preparation is the first critical step for the environment.

• Initial access: Done using a monitor and keyboard (GUI), but the goal is remote access via SSH.
• Network management: NetworkManager is used (a Linux service to manage connections) both through its graphical interface and via terminal.
• Static IP configuration:
◦ Problem: Trying to set the IP from the GUI caused loss of connectivity.
◦ Solution: nmcli (NetworkManager command-line interface) was used to configure the static IP (192.168.1.156) while keeping the SSH session active.

Note:
nmcli allows advanced network changes without relying on a graphical interface, which is essential on servers.

System Preparation and Dependencies

Before installing Nagios, the system must be validated and updated:

• Maintenance: Using apt update and apt upgrade to ensure that the package index and the software are up to date.
• Connectivity tests:
◦ ICMP (ping): To verify that the host has network access.
◦ DNS resolution: Confirm that the system translates domain names (like google.com) into IP addresses.

Software stack:
◦ Apache: Web server that loads the Nagios interface.
◦ PHP: Generates dynamic content (states, tables, alerts).
◦ SSL/TLS: Security protocol that encrypts communication and protects login credentials.

Note:
The “package index” can be understood as a catalog that shows which programs exist, which versions are available, and where to download them from.

Installation Troubleshooting

A key part of the project was resolving errors during dependency downloads:

• Mirror errors and IPv6: Downloads were failing because mirror servers were not accessible over IPv6.

Note:
The system’s internet protocol was not changed; instead, APT was forced to use IPv4 to stabilize downloads.

Nagios Core Installation

Unlike other software, Nagios Core was installed by compiling from source code.

• Process: Downloading the code, extracting it, configuring it, and running the make and make install commands.
• Integration: It was configured as a service managed by systemd so it starts automatically with the system.
• Security: A dedicated user (nagios) was created, Apache modules (cgi, rewrite) were enabled, and password authentication (htpasswd) was configured for the web panel.

Note:
Compiling from source means downloading the program as text, converting it into an executable, and then installing it manually.

Note:
A dedicated user is a system user created only for the program to run, not for people to log in, and with limited permissions.

The Plugin Challenge and Symbolic Links

The most important error occurred after installation: Nagios worked, but service checks failed (CRITICAL state).

• Cause: Installation method conflict. Nagios Core was installed manually from source, but the plugins were installed via apt (system packages). This caused a mismatch in execution paths.

Note:
Nagios was looking for the plugins in one folder, but the plugins were in another.

• Solution: Symbolic links were created to align the paths. This allowed Nagios to find the plugins where it expected them, without reinstalling all the software.

Note:
A symbolic link is like a “shortcut” that points to another file or folder.

• Result: Services changed from an error state to “OK” once the paths were fixed.

Summary of Demonstrated Skills

Linux administration: User management, services (systemd), and software compilation.

Networking: Static IP configuration, DNS resolution, and ICMP diagnostics.

Web security: SSL implementation and htpasswd authentication.

Troubleshooting: Error diagnosis through web interface messages and fixing file system paths.
Nagios web interface showing service status##
<img width="1912" height="1012" alt="Nagios Web Interface" src="https://github.com/user-attachments/assets/daee62d9-a6c0-4109-82b2-23d1887392ef" />
Services transitioning from CRITICAL to OK (initial plugin path mismatch) Before##
<img width="1913" height="850" alt="Captura de pantalla 2026-01-07 155147" src="https://github.com/user-attachments/assets/1586a423-8c03-4679-99be-3511a394e8ad" />
after##
<img width="1918" height="867" alt="Captura de pantalla 2026-01-07 154620" src="https://github.com/user-attachments/assets/b98b245a-5602-4fdb-b13d-f238f308bc7e" />

- Nagios service running and enabled at boot (`systemctl status nagios`##
<img width="1891" height="957" alt="Captura de pantalla 2026-01-05 174444" src="https://github.com/user-attachments/assets/6d9e20f2-2d35-4e0c-a37b-e8e6fcb3200f" />
