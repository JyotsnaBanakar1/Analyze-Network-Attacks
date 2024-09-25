Security Analyst Report

Overview
This repository contains the detailed report of a network security incident discovered while monitoring the web server for a travel agency. The agency’s website, which regularly advertises sales and promotions, was targeted by a cyberattack that overwhelmed the server, disrupting operations for both employees and customers. This document provides a comprehensive breakdown of the incident, analysis of the attack, and proposed next steps.

Incident Summary
Problem
The travel agency's web server, which employees use to access sales and vacation package data, became unresponsive, triggering an alert from the monitoring system. Upon investigation, the server was found to be overwhelmed with an abnormally high volume of TCP SYN requests coming from an unfamiliar IP address. This caused a connection timeout error, preventing access to the website.

Attack Detection
Using a packet sniffer, I captured and analyzed data packets between the web server and the source of the attack. The large volume of SYN requests suggested a SYN Flood Attack, a type of Denial-of-Service (DoS) attack where an attacker sends numerous SYN packets without completing the TCP handshake, overwhelming the server and preventing legitimate traffic from being processed.

Response Actions
Step 1: Temporary Mitigation
The web server was temporarily taken offline to allow it to recover from the overwhelming traffic.
The company’s firewall was configured to block the IP address that was sending the flood of SYN requests.

Step 2: Shortcomings of IP Blocking
Although the IP block restored the server’s functionality in the short term, the attacker could easily spoof different IP addresses, allowing them to bypass the block and continue the attack.
Communication to Management
Attack Type: SYN Flood Attack (Denial-of-Service)
The attack involves sending a large number of TCP SYN requests to the web server, overwhelming its capacity to respond.
This prevents legitimate traffic from reaching the server, causing disruptions for employees trying to access vacation package data.

Impact
Web Server Downtime: Employees and customers are unable to access the website due to the high volume of traffic and server overload.
Operational Disruption: The travel agency’s sales page, essential for employees to find vacation packages, was temporarily unavailable.
Next Steps and Recommendations
Implement SYN Cookies: Modify the TCP stack to use SYN cookies, which will help the server manage SYN flood attacks by preventing half-open connections from consuming resources.
Install an Intrusion Detection/Prevention System (IDS/IPS): Detect and block suspicious traffic, identifying patterns that suggest a DoS attack before it overwhelms the server.
Rate Limiting: Implement rate limiting to control the number of requests allowed from a single IP address, reducing the potential for overload.
Distributed Denial-of-Service (DDoS) Protection: Consider deploying a DDoS mitigation service to identify and block malicious traffic from multiple sources.
Log and Monitor Network Activity: Continuously monitor logs for unusual traffic spikes, allowing early detection of potential attacks.
Update Firewall Rules: Set up advanced firewall rules to detect and block IP spoofing attempts.

Conclusion
The SYN flood attack temporarily disrupted the web server’s functionality, affecting both employees and customers. While the immediate response mitigated the issue, a long-term solution involving proactive security measures is necessary to prevent similar attacks in the future. Recommendations have been provided to strengthen the company’s network security and protect against further attacks.
