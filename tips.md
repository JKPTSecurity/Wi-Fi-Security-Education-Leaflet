# Security Tips while using Wi-Fi network
This section provide you some tips on using and setting up your own Wi-Fi network.

There are three levels, each level target different group of people.

Please note that, key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL  NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED",  "MAY", and  "OPTIONAL" in this document are to be interpreted as described in [RFC 2119](https://tools.ietf.org/html/rfc2119).

## Level: Basic
All items in this level provide basic security when using or setting up your own Wi-Fi network. You MUST / SHOULD follow in order to protect yourself from script kids. If you are the person who manages any Wi-Fi network, you are the target of this level.


### 1. Use strong encryption for Wi-Fi connection (WPA2/WPA3)
#### When setting up your Wi-Fi network, choose WPA2/WPA3 (preferable) as the encryption for Wi-Fi connections.
Since data transmitted by Wi-Fi are through radio frequency, that is means, any person with a special Wi-Fi USB stick nearby can intercept your data. Although strong encryption cannot stop the hacker from stealing your data, it can increase the difficulty for the hacker to obtain your data in human-readable form. WEP should be treated as insecure and should use it only if WPA is not available.

#### Compliance:
* ISO/IEC 27001:2013 A.13.1.2 Security of network services
* PCI DSS v3.2.1 Section 2.1.1

##### References
Vanhoef, M. (2017). *Key Reinstallation Attacks: Breaking WPA2.* https://www.krackattacks.com/

SANS Institute. (n.d.). Enterprise Wireless Audit Checklist. *Security Consensus Operational Readiness Evaluation.* https://www.sans.org/media/score/checklists/EnterpriseWirelessNetworkAudit.pdf


### 2. Adopt static lease
#### The static lease is RECOMMENDED  to be deployed to ensure the administrators can identify the affected or involved machine easily and it could leave some crucial evidence for the investigators after incidents happened.
When security events or incidents happened, identifying affected hosts or the source of attacks quickly is critical for the administrators to take action to prevent further damage being made by the security events or incidents. They are also crucial for the investigators to collect evidence and reconstruct the incidents and do investigation on the incidents.


### 3. Never use vendor-default setting
#### Vendor-default setting MUST change as soon as possiable to prevent unautherized access. 
Most of the router/WI-FI access point default settings (for example, administrator pannel/Web panel username and password, wireless network password, and wireless network name can be found on the product website which most of it is public for everyone. Therefore, attackers can search for the WI-FI and admin pannel/Web panel username and password on google by search the wireless network name, since most of the default wireless network name is the model name of the router. Once attackers can access the network, they can simply login to the admin panel for changing all the config on the router.(physical security

#### Compliance:
* ISO/IEC 27001:2013 A.13.1.1 Network controls
* PCI DSS v3.2.1 Section 2.1.1


### 4. Set up at least a firewall, block all incoming connections by default if possible.
#### By block all incoming connection by default to prevent attack from the public network.
Set up a firewall and reject any incoming connections by default securing your computer is to protect it from attacks by outsiders. A firewall provides a barrier between your computer and the network, preventing unwanted traffic and authorized connections from outsiders.

#### Compliance:
* ISO/IEC 27001:2013 A.13.1.1 Network controls
* PCI DSS v3.2.1 Section 1.1 

##### References
Sourcedaddy. (n.d). *Blocking intruders with Windows firewall.* Sourcedaddy. https://sourcedaddy.com/windows-10/blocking-intruders-windows-firewall.html


### 5. Use AES(CCNP) only but not TKIP
#### If it is possible use AES rather than TKIP for improve the secrity.
To ensure users can connect to the Wi-Fi AP, there are two encryption types are TKIP and AES which provided by WPS2. However, TKIP is an older encryption standard used by the WPA standard, which has a vulnerability allowing attackers passthrough authentication to access the network. if the attacker success accessing the network, attacker can have more choice to perform different attack such as [ARP spoofing](attacks.md#4-ARP-spoofing) and [eavesdropping attack](attacks.md#3-Eavesdropping-attack) to capture the user network traffic.

#### Compliance:
* ISO/IEC 27001:2013 A.13.1.1 Network controls
* PCI DSS v3.2.1 Section 2.1.1


### 6. Upgrade router's firmware when available
#### Upgrade router's firmware when available can resistant new vulnerabilities.
Sometimes there are new vulnerabilities are found and they affect the network security, vendor may release a firmware update to patch the router. Upgrade router's firmware can protect your devices with knows vulnerabilities.


### 7. Use a strong password for Wi-Fi network and admin panel account
#### According to PCI DSS version 3.2.1 section 8.2.3 to 8.2.5, passwords MUST have a minimum length of at least seven characters and contain both numeric and alphabetic characters, MUST change at least once every 90 days, as well as MUST NOT the same as any of the last four passwords that have used.
A stronger Wi-Fi password makes the attacker use more time to crack your password. Moreover, if the attacker successfully accesses the network, s/he may further gain the root permission (the most significant permission) by cracking the admin panel login page. If the attacker successfully login into the admin panel, it means s/he can control your network. Thus, the account password for the admin panel and the network MUST be strong.

#### Compliance:
* ISO/IEC 27001:2013 A.9.2.3 Management of privileged access rights
* ISO/IEC 27001:2013 A.9.2.4 Management of secret authentication information of users
* ISO/IEC 27001:2013 A.9.4.3 Password management system
* ISO/IEC 27001:2013 A.13.1.1 Network controls
* PCI DSS v3.2.1 Section 8.2.3
* PCI DSS v3.2.1 Section 8.2.4

##### References
PCI Security Standards Council. (2018). Payment Card Industry (PCI) Data Security Standard Requirements and Security Assessment Procedures. https://www.pcisecuritystandards.org/documents/PCI_DSS_v3-2-1.pdf


### 8. Use an SSID that will not give away excess information
#### Don't use your personal information such as home location or phone number as SSID
Since the router will broadcast the service set identifier (SSID, i.e. wireless network name) by default, anyone in the range of the wireless signal can see your wireless network name. Excess information means you are providing information for an attacker to perform further attacks such as social engineering and phishing.


### 9. Backup the configuration file of the router regularly.
#### By backup the configuration file regularly preventing when router failure all the setting have to config again.
Backup the configuration file regularly (for example, Once per month, Once per week), when router failure, you can simple use a new router and upload the configuration file and restore all the config.

#### Compliance:
* ISO/IEC 27001:2013 A.12.3.1 Information backup


## Level: Intermediate
All items in this level provide advanced security when using or setting up your own Wi-Fi network. You MUST / SHOULD follow in order to protect yourself from hackers who have the basic hacking skills. If you are the person who manages any Wi-Fi network and wants the network to be very secure, you are the target of this level.

### 10. Use WPA2-Enterprise with TLS if possible
#### EAP-TLS is the safest authentication method. Besides authentication, it can also integrate with other network services to carry out authorization and accounting. So, use EAP-TLS.
To ensure end users can connect to the Wi-Fi AP, two most common Wi-Fi authentication method are Pre-Share Key(PSK) and EAP-MSCHAPv2. However, both PSK and MSCHAPv2 have their weaknesses. By using PSK, attackers can obtain the hashed PSK by any means and crack the hash value to get the password of the AP. And because MSCHAPv2 is the only one that supports most of the platforms in the world (for example, Linux, Windows, macOS, iOS, and  Android), MSCHAPv2 is widely adopted in WPA2-Enterprise Wi-Fi. However, the hash function behind it is NTLM, which is just simply an MD4 (even worse than MD5), once the attacker gets the hash value during the 4-way handshake, they can crack the hash really fast. Although a long PSK or password of the credential will eliminate the problem, it still leaves an attack factor to attacks. EAP-TLS uses the client certificate to autheBlocking intruders with Windows firenticate the client device, and it is super difficult to forge a valid client certificate. Therefore, EAP-TLS will be the most secure authentication method.

#### Compliance:
* ISO/IEC 27001:2013 A.13.1.2 Security of network services
* PCI DSS v3.2.1 Section 2.1.1

##### References
user1786283. (2013). Answer to *How to calculate NTLM hash in python?* Stack Overflow.https://stackoverflow.com/questions/15603628/how-to-calculate-ntlm-hash-in-python

Intel Corporation. (n.d.). *802.1X Overview and EAP Types.* Intel. https://www.intel.com/content/www/us/en/support/articles/000006999/network-and-i-o/wireless.html

SANS Institute. (n.d.). Enterprise Wireless Audit Checklist. *Security Consensus Operational Readiness Evaluation.* https://www.sans.org/media/score/checklists/EnterpriseWirelessNetworkAudit.pdf


### 11. Perform hardening according to official or industrial hardening standard
#### Hardening means reducing security risk by implementing security configurations, such as disable or remove unnecessary functions, accounts or services. You can perform hardening according to the official document from the vendor, or industrial standards like CIS Benchmarks.
Unnecessary functions or services may provide opportunities for the attacker to gain access to a system. By disabling unnecessary functions or service, the risk of unknown functions being used by an attacker can be reduced.

#### Compliance:
* ISO/IEC 27001:2013 A.9.2.4 Management of secret authentication information of users
* ISO/IEC 27001:2013 A.9.3.1 Use of secret authentication information
* PCI DSS v3.2.1 Section 2.1.1


### 12. Restrict the range of the wireless signal at an appropriate level
#### To avoid unknown individuals to access your network, you MAY restrict the range of the wireless signal.
A bigger range of wireless signals means more people can try to access your network. Therefore, it is better to restrict the range of the wireless signal at an appropriate level only known individuals can access. Moreover, you MAY choose not to broadcast the SSID.

#### Compliance:
* ISO/IEC 27001:2013 A.9.1.2 Access to networks and network services


### 13. Enable MAC filtering if possible
#### MAC filtering is a technique of access control. Its function like a whitelist or blacklist, can be used to permit and deny access to the network.
By configuring only the allowed devices can access the network, or only some devices cannot access the network, it can prohibit unauthorized access.


### 14. Detect and identify all authorized and unauthorized wireless AP on a quarterly basis
#### Detecting and identifying all authorized and unauthorized wireless APs can help you discover the evil twins attack.
By detecting and identifying all authorized and unauthorized wireless AP, you have less chance to connect to another unknown AP. Furthermore, identifying all authorized APs can help you [create an inventory list](tips.md#22-maintain-an-inventory-of-authorized-wireless-access-points), [draw the network diagram](tips.md#20-plan-the-architecture-of-wlan-before-deployment) and [perform the audit](tips.md#23-perform-security-assessments-of-wlan-in-timely-basis).

##### References:
ISO/IEC 27001:2013 A.12.7.1 Information systems audit controls


### 15. If possible, consider OpenWrt as router's firmware
#### There are many advantage of usign OpenWrt as router's firmware
OpenWrt will actively update so vulnerabilities will remove shortly after they are discovered. OpenWrt, provide a higher ability to you for configuring each setting on the router, vendor firmware usually include some limitation on the configuration.

##### References:
Tmomas. (2020). *Reasons to use OpenWrt.* OpenWrt. https://openwrt.org/reasons_to_use_openwrt


### 16. If possible don't setting up guest network, if needed totally isolate them
#### Most of the guest network settings provided by vendor firmware are not separate the internal network and the guest network. Therefore, if attackers have access to the guest network, they may also have a chance to perform attacks on the internal network.
By totally ISO/IEClate the internal network and the guest network is much secure than using guest network, most of the guest network is using the same network that you are using, so there is still have chance for attacker connect to the guest network and able to perform the attack inside the network. By sperate it correctly there are no chance for the attacker perform attack to your internal devices.


### 17. Secure all APs in physical manner
#### Lock all APs in a container or even put a security camera to monitor the physical status of the APs.
Without physically secure all AP, there is always a big threat that attackers can do hardware-level hacking and compromise the AP or even perform further Advanced Persistent Threat attack. Also, it is a big topic on different compliances. In ISO/IEC 27001, A.11 is the section dedicated to physical security. And in PCI-DSS Requirement 9 is also the section dedicated to physical security. Without securing the APs physically, the organization may fail the information security audit.

#### Compliance:
* ISO/IEC 27001:2013 A.11.2.1
* ISO/IEC 27001:2013 A.11.2.3
* ISO/IEC 27001:2013 A.11.2.4
* ISO/IEC 27001:2013 A.11.2.8
* PCI-DSS v3.2.1 Section 9.1.3
* PCI-DSS v3.2.1 Section 9.1.1
* PCI-DSS v3.2.1 Section 9.5

##### References:
International Organization for Standardization. (2013). *Information technology — Security techniques — Information security management systems — Requirements*

PCI Security Standards Council. (2018). *Payment Card Industry (PCI) Data Security Standard Requirements and Security Assessment Procedures.* https://www.pcisecuritystandards.org/documents/PCI_DSS_v3-2-1.pdf


### 18. If certificate is not possible, strong password policy should be established
#### If WPA2-Enterprise with TLS is not possible in the environment, a strong password policy can ensure all password created is secure, hence it can prevent [the brute force attack mentioned above](tips.md#10-use-wpa2-enterprise-with-tls-if-possible).
A strong password policy can ensure the strength of the password created by personnel in the environment for whatever reason. By creating a strong password, even the attacker employed hundred and thousand of RTX 3060 Ti GPU it can ensure the cost needed for cracking the hash value is super expensive in terms of time and electricity bill. The criteria of a strong password can be found in [here](tips.md#7-use-a-strong-password-for-wi-fi-network-and-admin-panel-account).

#### Compliance:
* ISO/IEC 27001:2013 A.9.4.3 Password management system
* PCI-DSS v3.2.1 Section 2.1.1
* PCI-DSS v3.2.1 Section 8.2.3
* PCI-DSS v3.2.1 Section 8.2.5

##### References:
PCI Security Standards Council. (2018). *Payment Card Industry (PCI) Data Security Standard Requirements and Security Assessment Procedures.* https://www.pcisecuritystandards.org/documents/PCI_DSS_v3-2-1.pdf

SANS Institute. (n.d.). Enterprise Wireless Audit Checklist. *Security Consensus Operational Readiness Evaluation.* https://www.sans.org/media/score/checklists/EnterpriseWirelessNetworkAudit.pdf


## Level: Advanced
All items in this level provide extreme security when using or setting up your own Wi-Fi network. You MUST / SHOULD follow in order to protect yourself from most of the hackers. If you are the person who manages any corporate Wi-Fi network or your network needs to comply with some compliances, you are the target of this level.
### 19. Deploy Intrusion Detection Systems (IDS)
#### Intrusion detection systems can actively or passively monitor your Wi-Fi network. When security events or incidents happened, alert you at the earliest time.
An ounce of prevention is worth a pound of cure. By using IDS, you can give responses to and security events and incidents as quickly as possible. IDS can also generate event logs for the incident response or compliance need. One significant feature or event before the actual Wi-Fi attack comes is the Wi-Fi de-authentication attack, it is a DoS attack but usually, the purpose of performing this attack is to get the Wi-Fi authentication information, which may grant the hacker access to the Wi-Fi network. If you want to know more about this attack, check it out [here](attacks.md#1-wi-fi-deauthentication-attack)!

AD:

JKPTSecurity noticed that tools for monitoring Wi-Fi de-authentication attacks are mostly proprietary, therefore, we developed an open source Wi-Fi disconnection detection system. It is capable to detect de-authentication and disassociation signals and alert you or administrators instantly for you to take action at the early stage of Wi-Fi attacks. You may want to check that out [here](https://github.com/JKPTSecurity/CCIT4077). It is available for OpenWRT and other Linux distribution.

#### Compliance:
* ISO/IEC 27001:2013 A.13.1.1 Network controls
* PCI DSS v3.2.1 Section 11.4

##### References
PCI Security Standards Council (2018). *Payment Card Industry (PCI) Data Security Standard Requirements and Security Assessment Procedures.* https://www.pcisecuritystandards.org/documents/PCI_DSS_v3-2-1.pdf

SANS Institute. (n.d.). Enterprise Wireless Audit Checklist. *Security Consensus Operational Readiness Evaluation.* https://www.sans.org/media/score/checklists/EnterpriseWirelessNetworkAudit.pdf


### 20. Plan the architecture of WLAN before deployment 
#### After planning the architecture of WLAN, you MAY draw a network diagram to have a better understanding of the WLAN environment.
Clear architecture and network diagram(s) help you understand fully at a glance and hence help you troubleshoot the network problem. In addition, it helps you identify all the devices in the WLAN in order to [create an inventory list](tips.md#22-maintain-an-inventory-of-authorized-wireless-access-points) and [perform the audit](tips.md#23-perform-security-assessments-of-wlan-in-timely-basis).

#### Compliance:
* PCI-DSS v3.2.1 Section 1.1
* ISO/IEC 27001:2013 A.12.7.1 Information systems audit controls


### 21. Ensure all APs have the same configuration and audit them periodically
#### Use the same config when you are configuring the AP if possible. After that, review the config on a timely basis.
Using the same config can help you manage and review the AP config more easily as all the configurations are the same. Configuration management and audit are the elements of information security, [reviewing the configuration periodically](tips.md#23-perform-security-assessments-of-wlan-in-timely-basis) can avoid unauthorized changes.

#### Compliance:
* PCI-DSS v3.2.1 Section 1.1
* PCI-DSS v3.2.1 Section 10.1
* ISO/IEC 27001:2013 A.12.7.1 Information systems audit controls


### 22. Maintain an inventory of authorized wireless access points
#### An inventory SHOULD be created, by using a database or a CSV file, which contains all information about all APs.
An inventory SHOULD be created by using a database or a CSV file, because an inventory list is the basic to an information security management system. It can help to make sure proper protection of all APs takes place and keep track of those APs to identify missing or [Evil Twins APs](attacks.md#5-evil-twins-attack). In ISO/IEC 27001, the inventory list is the control 8.1.1. As the Plan-Do-Check-Act cycle illustrates, if an organization does not has an inventory, all the subsequent controls will never be implemented successfully. The inventory list should be kept up to date as always. Statement of Applicability, Acceptable Use Policy, etc. are all depend on the inventory list.

#### Compliance:
* ISO/IEC 27001:2013 A.8.1.1 Inventory of assets
* PCI-DSS v3.2.1 Section 1.1.3
* PCI-DSS v3.2.1 Section 2.4
* PCI-DSS v3.2.1 Section 9.9.1
* PCI-DSS v3.2.1 Section 11.1.1

##### References
International Organization for Standardization. (2013). *Information technology — Security techniques — Code of practice for information security controls*

PCI Security Standards Council (2018). *Payment Card Industry (PCI) Data Security Standard Requirements and Security Assessment Procedures.* https://www.pcisecuritystandards.org/documents/PCI_DSS_v3-2-1.pdf


### 23. Perform security assessments of WLAN in timely basis
#### Performing review on WLAN authentication and authorization methodology. If any scheme has been found broken during the assessment, replace it quickly.
By performing security assessments, you can keep your WLAN in control and identify vulnerability and threats or even on-going Advanced Persistent Threat. It is also crucial for an organization to comply with compliance. For example, both ISO/IEC 27001 and PCI-DSS require organizations to have regular security assessments. Those assessments can be vulnerability scanning, penetration testing, and review of the information security management system.

#### Compliance:
* ISO/IEC 27001:2013 A.18.2.1 Independent review of information security
* ISO/IEC 27001:2013 A.18.2.3 Technical compliance review
* PCI-DSS v3.2.1 Section 11.2.1
* PCI-DSS v3.2.1 Section 11.2.3
* PCI-DSS v3.2.1 Section 12.2

##### References
SANS Institute. (n.d.). Enterprise Wireless Audit Checklist. *Security Consensus Operational Readiness Evaluation.* https://www.sans.org/media/score/checklists/EnterpriseWirelessNetworkAudit.pdf

International Organization for Standardization. (2013). *Information technology — Security techniques — Information security management systems — Requirements*

PCI Security Standards Council. (2018). *Payment Card Industry (PCI) Data Security Standard Requirements and Security Assessment Procedures.* https://www.pcisecuritystandards.org/documents/PCI_DSS_v3-2-1.pdf


### 24. Radius shared secret should be different across different devices
#### Each network device (radius clinet) SHOULD set up a different shared secret, preventing the shared secret leakage lead to all other devices connection is vulnerable
A shared secert is basically an encrpytion key that is known to the RADIUS client, it used to encrypt authentication credentials and data. All the device on the network SHOULD have a unqie shared secret, because if only one shared secret is setuped, when an attacker cracked it all the others Radius clinet account credentials can e cracked. Similar situation when all ur website account use the same password, when the password is compromise, all your other account may have chance for login by attackers.

##### References
Posey, B. (2005). *SolutionBase: Best practices for implementing RADIUS.* Techrepublic. https://www.techrepublic.com/article/solutionbase-best-practices-for-implementing-radius/


### 25. Implement incident response procedures in the event unauthorized wireless access points are detected
#### By Implement incident response procedures, you can handle it quickly and minimize losses.
Incident response procedures SHOULD be created, which should list out when different unexcepted event happens on the wireless network. For example, an unauthorized device connected to the network, the wireless networking getting DDOS attack, the wireless access points suddenly unavailable for use, each scenario MUST have the different procedures.

#### Compliance:
* ISO/IEC 27001:2013 A.16.1.1 Responsibilities and procedures

##### References
International Organization for Standardization. (2013). *Information technology — Security techniques — Information security management systems — Requirements*
