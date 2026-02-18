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
