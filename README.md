# SonicWall-Firewall- Project
# Project 1: Creating and Enforcing Firewall Rules and Policies

# Overview:
This project demonstrates the design, implementation, and testing of firewall rules and policies on a SonicWall firewall to secure a corporate network. The goal is to control traffic between LAN and WAN, block unauthorized access, and enforce security policies while maintaining normal operations for allowed traffic. The project covers blocking specific websites, ICMP (ping) requests, Remote Desktop (RDP) traffic, and DNS queries, providing hands-on experience in firewall configuration, traffic monitoring, troubleshooting, and best practices for enterprise network security.

# Project Objectives:

- Learn to create, enforce, and test firewall rules.

- Understand traffic flow and how firewall policies control it.

- Implement rules to block specific services while allowing normal traffic.

- Practice safe testing procedures in a controlled environment before production deployment.

- Document and troubleshoot firewall policies for real-world scenarios.

# Test Scenarios

# Test 1: Block a Website

# Objective: Block access to chase.com while allowing access to all other websites.

# Setup and Configuration:
- Create a firewall rule specifying chase.com as the blocked destination.
- Apply the rule to the LAN → WAN zone.
 
# Verification:
- Users are unable to access chase.com from their browser within the company network.
- Access to all other websites functions normally.
- Logs confirm that the firewall rule is actively blocking the traffic.

# Conclusion:
This test demonstrates the firewall’s ability to enforce policies that control website access, ensuring compliance with company security guidelines while allowing normal web traffic.

# Test 2: Block ICMP (Ping) Requests

# Objective: Block ICMP requests to a specific IP (e.g., 1.1.1.1) while allowing all other traffic.

# Setup and Configuration:
- Create a firewall rule to block ICMP traffic from the LAN to the specified IP.
  
# Verification:
- Attempts to ping the blocked IP fail.
- Other traffic, such as HTTP/HTTPS, continues to work normally.
- Logs confirm the ICMP traffic is being blocked.

# Conclusion:
This test shows how firewall rules can prevent unauthorized or unnecessary network probes while maintaining normal operations, demonstrating effective traffic control and monitoring.

# Test 3: Block RDP (Remote Desktop Protocol)

# Objective: Block RDP traffic on port 3389 from LAN to WAN while allowing other traffic.

# Setup and Configuration:
- Create a firewall rule blocking TCP port 3389 for LAN → WAN.

# Test and Verification:
- Open Remote Desktop (mstsc.exe) and attempt to connect to any public IP. The connection should fail.

# Conclusion:
This test confirms that RDP traffic can be restricted to prevent unauthorized remote access while other network services remain operational. It reinforces the importance of proper rule enforcement and verification.

# Test 4: Block DNS Queries

# Objective: Block all DNS (Port 53) queries from a PC to prevent domain name resolution while allowing other traffic.

# Setup and Configuration:

- Create a firewall rule blocking TCP and UDP port 53 from the PC to external DNS servers.

# Important: Place this rule at the top of the LAN → WAN rules list to ensure it is evaluated first.

# Verification:
- Open a web browser and attempt to visit any website (e.g., cnn.com). The request fails, confirming DNS queries are blocked.
- Other types of traffic are unaffected.

# Conclusion:
- This test demonstrates the firewall’s ability to control critical services like DNS, ensuring unauthorized resolution requests are blocked while maintaining overall network functionality.

# Firewall Rule Best Practices:

- Place Deny Rules at the Top: Firewall rules are processed top-down. Always position deny or block rules above allow rules to ensure they are enforced correctly.

- Define the Source Carefully: Use “Source: Any” to block traffic from all internal devices or specify individual IPs/Address Objects for precise control.

- Test Each Rule in a Controlled Environment: Verify that rules block or allow the intended traffic. Always perform testing in a lab or staging environment before applying rules to production. Check firewall logs to confirm the rule is functioning correctly.

- Clean Up Temporary Rules: Remove test rules and objects after verification to keep the configuration organized. Keep permanent security rules intact.

- Use Address and Service Objects: Simplifies rule management, improves readability, and reduces configuration errors.

- Enable Logging for Critical Rules: Monitor traffic patterns, detect anomalies, and troubleshoot effectively.

- Regularly Review Rules: Periodically audit firewall rules to remove redundant, obsolete, or conflicting entries.

- Implement the Principle of Least Privilege: Allow only the minimum required access for users, applications, and devices.

- Backup Configuration: Take a backup before making significant changes for easy recovery.

- Monitor and Update Firmware: Keep firewall firmware up to date to protect against vulnerabilities.

- Test Changes Before Production: Always validate rules and policies in a test or staging environment to prevent disruption in the production network.

# Key Takeaways:

- Firewall rules are essential for securing network traffic and enforcing company policies.

- Testing and verification in a controlled environment prevents mistakes from affecting production networks.

- Practical skills gained include policy creation, traffic monitoring, troubleshooting, and application of best practices.

- This project provides a strong foundation for enterprise network security management and administration.

 # Conclusion: 
 This project demonstrates hands-on experience in designing, implementing, and testing firewall rules and policies to secure an enterprise network. By creating rules to block specific websites, ICMP requests, RDP traffic, and DNS queries while allowing other traffic, the project highlights the importance of precise rule definition, policy enforcement, and thorough testing.

Key skills gained include firewall configuration, traffic monitoring, troubleshooting, and application of best practices in a safe, controlled environment. The project reinforces the need to validate rules before production deployment, maintain organized configurations, and apply the principle of least privilege. Overall, it provides a strong foundation in network security and prepares for real-world enterprise administration and policy management scenarios.

# Project 2: Configuring SonicWall SSL VPN for Remote Access

# Overview:
This project demonstrates the design, implementation, and testing of a secure SSL VPN on a SonicWall firewall to provide encrypted remote access for users. SSL VPN (Secure Sockets Layer Virtual Private Network), also known as a point-to-site VPN, allows individual devices to securely connect to a corporate network over the internet. Unlike a site-to-site VPN, which connects entire networks, SSL VPN is ideal for remote employees, traveling staff, or home workers who need access to internal company resources such as applications, file servers, databases, and RDP-enabled machines.

# Real-World Use Cases:

- Employees working from home accessing internal HR, CRM, or project management applications securely.

- Traveling staff connecting to company file shares and RDP-enabled PCs from hotels or client sites.

- IT staff performing maintenance, troubleshooting, or remote administration on internal servers.

- Temporary contractors needing restricted access to specific internal resources for limited periods.


# Example Scenario:

# A company has offices in Sydney, Melbourne, and Perth. Remote employees and traveling staff need access to:

- Internal databases for reporting and analytics.

- RDP-enabled office PCs to manage applications.

- Shared network drives and company intranet services.

- Internal applications without exposing sensitive data over the public internet.

- SSL VPN ensures that all traffic between the client device and corporate network is encrypted, protecting sensitive data even over public networks.


# Project at a Glance:

- Enables secure, encrypted remote access with SonicWall SSL VPN over WAN port 443.

- Assigns a dedicated SSL VPN IP pool (192.168.6.70–192.168.6.90) and routes to the internal subnet X0 (192.168.6.0/24).

- Grants access via the SSLVPN Services group and validates connectivity using NetExtender and RDP.


# Steps and Configuration

# Step 1: Prepare the Firewall

- Log in to the SonicWall firewall and navigate to the Manage section to confirm readiness for SSL VPN deployment.

- Ensure the firewall dynamically assigns IP addresses from 192.168.6.20 to 192.168.6.50 on the X0 interface, providing VPN clients proper IP allocation.

# Step 2: Enable SSL VPN

- Enable SSL VPN on the WAN zone, set the port to 4433, and choose Local Domain for user authentication.

# Path: Manage → VPN → SSL VPN → Server Settings → Configure WAN, Port 4433, Local Domain → Accept.

# Step 3: Configure SSL VPN Client Network

- Select the SSLVPN zone and create a new IPv4 network for SSL VPN clients.

- Assign IP addresses 192.168.6.70–192.168.6.90 for remote users.

- Add the X0 subnet to the SSL VPN client routes so users can access internal resources.

- Save the configuration.

# Step 4: Create SSL VPN Users

- Create a local user named John with a secure password.

- Add the user to the SSLVPN Services group to grant VPN access.

- Include the X0 subnet in the VPN access list.

- Save all settings.

# Step 5: Install and Configure NetExtender Client

- Disconnect any other VPN sessions.

- Log in to SonicWall Virtual Office using the new user credentials.

- Create an RDP bookmark with the target PC’s IP address and credentials.

- Download and install the NetExtender client.

- Accept license agreements and complete installation.

# Step 6: Connect to SSL VPN

- Open NetExtender, enter server details and credentials, and click Connect.

- Accept the certificate prompt (“Always Trust”).

- Verify the SSL VPN connection shows both SonicWall public IP and the private IP assigned to the client (e.g., 192.168.6.70).

- Confirm connectivity to internal network 192.168.6.0/24.

  # Verification and Testing:

- Confirm NetExtender adapter shows correct VPN IP and subnet.

- Test connectivity to RDP-enabled PCs, file servers, and internal applications.

- Ensure encrypted traffic flows correctly and routes are accessible.

- Review firewall logs to detect and resolve authentication or routing issues.

# Best Practices:

- Use a Dedicated IP Pool: Prevent IP conflicts between VPN clients and internal LAN.

- Test in a Controlled Environment: Validate setup before production deployment.

- Add Internal Routes Carefully: Only allow access to required subnets.

- Assign Users to Specific VPN Groups: Control resource access with SSLVPN Services groups.

- Monitor Logs and Connectivity: Track VPN sessions, authentication, and traffic patterns.

- Keep Client Software Updated: Use the latest NetExtender version for security.

- Verify Security Settings: Enforce strong passwords and proper encryption.

- Audit VPN Configurations Regularly: Remove unused accounts, routes, and policies.

- Backup Configurations: Ensure quick recovery from misconfigurations.

- Follow Principle of Least Privilege: Users should only access what they need.


 # Key Takeaways:

- SSL VPN provides secure remote access as if the user were on-site.

- Gained hands-on experience with VPN setup, IP pool management, client configuration, and internal routing.

- Testing and verification ensure smooth operations and security compliance.

- This project reinforces the importance of group management, firewall policies, and systematic troubleshooting.

# Conclusion:
Configuring SSL VPN on SonicWall provides a secure and reliable method for remote employees to access internal resources. By enabling SSL VPN on the WAN interface, creating a dedicated IP pool, adding internal routes, and assigning users to the SSLVPN Services group, organizations ensure encrypted communication and proper connectivity. Systematic troubleshooting, monitoring, and regular audits maintain smooth operations and strengthen network security, making this setup ideal for supporting remote work efficiently and securely.
