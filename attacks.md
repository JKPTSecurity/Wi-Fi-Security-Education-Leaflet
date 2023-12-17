# Introduction to common Wi-Fi attacks
This section introduce some common Wi-Fi attacks to you while using Wi-Fi network.

There are three categories, they are Denied of Service, Man in the Middle and Others.

Please note that, key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL  NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED",  "MAY", and  "OPTIONAL" in this document are to be interpreted as described in [RFC 2119](https://tools.ietf.org/html/rfc2119).


## Category: Denial of Service (DoS)
DoS is a common attack method use by hackers. Usually, when a service is attacked by (D)DoS, their availability will be suffered, in other words, service users will cannot access the intended service(s). Beside, DoS can also be the first step to further and deeper attacks.


### 1. Wi-Fi deauthentication attack
#### Attackers can keep sending a disconnection signal to clients, hence, the clients cannot connect to the Wi-Fi network. However, isn't it boring to just preventing clients from connecting to the Wi-Fi network? So, attackers MAY perform disconnection attacks with the 4-way handshake of WPA and further brute-force attack to steal the key to the Wi-Fi network.
802.11 defined two types of management frames that can use to disconnect a client forcibly, which are deauthentication (0x0c) and disassociation (0x0a). With unprotected management frames, anyone can forge a management frame with the subtype of 0x0c/0x0a to force any associated clients to disconnect. In 0x0c/0x0a management frame, it requires mainly two pieces of information, one is the base SSID, another is the client MAC address. However, attackers only need to know the base SSID of the AP because they can set the client MAC address to FF:FF:FF:FF:FF to broadcast the disconnection signal. After disconnecting clients, attackers can perform further attacks, such as [Authentication Cracking](attacks.md#6-authentication-cracking-wep-wpa-wpa2) and [Evil Twins Attack](attacks.md#5-evil-twins-attack). Simply speaking, fake disconnection notification will sent to spoof your device to trust the attacker.

#### Countermeasure:

#### If provided by the vendor, enable protected management frames feature
* Some vendors provide the 802.11w feature to increase the security of management frames, by enabling them, attackers cannot send forged management frames to disconnect the clients. However, not all devices support this.

#### Adopt Intrusion Detection/Prevention System
* Using IDS/IPS is one of the solutions. The system can stop or alert administrators in the first place when the attacks are being performed. Some proprietary router or AP already shipped with the IDS/IPS to tackle the deauthentication attack. For open source solution, you may want to check out [Open Wi-Fi Disconnection System](tips.md#19-deploy-intrusion-detection-systems-ids).

##### References
Wi-Fi deauthentication attack. (2021, February 08). In *WikiPedia*. https://en.wikipedia.org/wiki/Wi-Fi_deauthentication_attack


## Category: Man in the Middle
A man-in-the-middle (MitM) attack is an attack where an attacker intercepts communications between parties to pretend or to listen in on one of the sides. For example, Alice and Bob are chatting, Eve listens in on them, or even Eve can pretend as Alice to chat with Bob.


### 2. Session hijacking
#### Session hijacking is one of the MitM attacks, where a user session is being taken over by an attacker. It commonly happens to browser sessions and web applications.
This is because when you login into some web applications, such as online banking, the server will set a temporary session cookie (cookie is a web technology) in the browser to remember that you are currently logged in and authenticated. If these cookies were captured by the attacker or sent to the attacker, the attacker can perform any actions that you are authorized to do.

#### Countermeasure:

#### Don't click on any suspicious link
* You are RECOMMENDED to use some tools to check the link before you click on it if you think the link is suspicious.
* This is the most effective method to prevent session hijacking.

#### Don't perform login action on any website without HTTPS
* A website without HTTPS in the URL means the transmission of the data is not encrypted.
* An attacker can capture what you send to the server, in other words, cookies can also be captured.
* The attacker can check whether there is the account information inside easily as it does not have any encryption.
* Most of the modern browsers will warn you when you access a website without HTTPS connection, an "insecure" wording will be shown next to the URL in order to remind you.

##### References
Banach, Z. (2019, August 22). *What Is Session Hijacking: Your Quick Guide to Session Hijacking Attacks.* netsparker. https://www.netsparker.com/blog/web-security/session-hijacking/

OWASP Foundation, Inc. (n.d). *Session hijacking attack.* OWASP. https://owasp.org/www-community/attacks/Session_hijacking_attack


### 3. Eavesdropping attack
#### Eavesdropping attack is also similar to sniffing or snooping attack, attacker route user network traffic to the attacker machine to capture all victim's packets passthrough.
Attackers generally will weaken the connection from the target to the server, so they can reroute the network traffic from the target send to the attacker's machine first before it sends to the server, also they will use software to capture all the network traffic which pass through the machine.

#### Countermeasure:

#### Avoid using public network
* Use of public network (for example network in coffee-shop or resturant) should be avoid specially for sensitive transactions.

#### Don't perform login action on any website without HTTPS when you are connected to public Wi-Fi
* A website without HTTPS in the URL means the transmission of the data is not encrypted.
* The attacker can check whether there is the account information inside easily as it does not have any encryption.
* Well-known browsers will warn you when you access a website without HTTPS connection, an "insecure" wording will be shown next to the URL in order to remind you.

##### References
Frankenfield, J. (2020). *Financial Technology & Automated Investing Financial Technology.* Investopedia. https://www.investopedia.com/terms/e/eavesdropping-attack.asp


### 4. ARP spoofing
#### ARP spoofing is an attack that exploits the ARP protocol vulnerability to reroute user traffic pass through the attacker machine to capture the user traffic.
ARP protocol is used as a map, which maps between MAC address and IP address in the network. It used to determine the destination MAC addresses of the network nodes so the machine can connect to the network. When an attacker has access to the network, they will use spoofing software to send out forged ARP response, the forged APR response fool the devices in the network which lead the arp table (which maps between MAC address and IP address) on the router and the victim's machine change, so when any send data traffic send between the victim's machine and the router it will pass through the attacker machine first, therefore the attacker can use a sniffer to capture the traffic passthrough.

#### Countermeasure:

#### Avoid using public network
* Use of public network (for example network in coffee-shop or resturant) should be avoid specially for sensitive transactions. Since attacker may also have the access of the public network, so they can perfrom the attack easily.

#### Use static ARP
* Set up static ARP by yourself, so when there is an anttacker perfrom APR spoofing attack, your machine will simple auto ignore the forged ARP respone.

#### Don't perform login action on any website without HTTPS
* A website without HTTPS in the URL means the transmission of the data is not encrypted.
* The attacker can check whether there is the account information inside easily as it does not have any encryption.
* Well-known browsers such as Google Chrome will warn you when you access a website without HTTPS connection, an "insecure" wording will be shown next to the URL in order to remind you.

##### References
Imperva. (n.d) *ARP Spoofing.* Imperva. https://www.imperva.com/learn/application-security/arp-spoofing

ARP spoofing. (2021, February 01). In *WikiPedia*. https://en.wikipedia.org/wiki/ARP_spoofing


### 5. Evil twins attack
#### An evil twin attack is an attack where an attacker sets up a Wi-Fi network and configures the network name to be the same as or look like a usual Wi-Fi network.
If you connected to the network before, your device will auto-connect to the network if you are in the network coverage. In this situation, you may not be affected by the evil twin attack. However, the attacker can use DoS attacks such as [Wi-Fi deauthentication attack](attacks.md#1-Wi-Fi-deauthentication-attack) to force you to disconnect from the network. The DoS attack can be as long as a couple of hours. When your device cannot connect to the network automatically, most of the users will try to reconnect to the network manually. At that time, if the user does not realize there is an evil twin attack, s/he may connect to the network set up by the attacker. As a result, the attacker can check that unencrypted information whether there is sensitive information inside or even downgrade your encrypted traffic to unencrypted traffic.

#### Countermeasure:

#### Use mobile data instead of public Wi-Fi network if possible
* Since the evil twin attack is a Wi-Fi attack, it is not working on mobile data.

#### Use [EAP-TLS](tips.md#10-use-wpa2-enterprise-with-tls-if-possible) if possible
* WPA2 is a Pre-shared key (password) based authentication methodology, while EAP-TLS is certificate based.
* It required the user to use the certificate to perform the authentication.
* Since the certificate is pre-distributed, it can avoid unauthorized individuals to access the network if no one leaks the certificate.
* EAP-TLS can also be used in the access control system, such as the access card system.

##### References
Green, E. (2019, April 8). *How to stop your phone’s Wi-Fi from revealing where you live*. NordVPN. https://nordvpn.com/blog/wifi-scanning-hack/


## Category: Others


### 6. Authentication cracking (WEP, WPA, WPA2)
#### Authentication cracking is an attack where an attacker captures the authentication traffic and crack it by brute force in order to gain the access permission of the network.
Wireless devices such as smartphones are required to broadcast the signal so as to transfer data. Therefore, the attacker can capture all the traffic including the pre-shared key (Wi-Fi password) if s/he is near enough to you. Although the key is encrypted, the attacker can crack it by brute force. Apart from that, an attacker can perform DoS attacks such as [Wi-Fi deauthentication attack](attacks.md#1-Wi-Fi-deauthentication-attack) first to force the user to disconnect from the network, and then capture the authentication traffic when the client is trying to reconnect.

#### Countermeasure:

#### Use the latest encryption standard if possible
* The latest encryption standard is WPA3, however, some old home or enterprise routers only provide WPA2.
* Therefore, you SHOULD use the latest encryption when you configure the Wi-Fi password in the admin panel.

#### Use a strong Wi-Fi password
* A stronger Wi-Fi password means the attacker needs more time to decrypt the password.
* Even if s/he captured the traffic, it is not easy to decrypt the password in a short time.
* For the definition of a strong password, please refer to another leaflet [Security Tips while using Wi-Fi network](tips.md#7-use-a-strong-password-for-wi-fi-network-and-admin-panel-account). 
* Remember, a strong Wi-Fi password with an old encryption standard is meaningless.
* You SHOULD use the latest encryption standard and a strong Wi-Fi password at the same time.

##### References
Cracking of wireless networks. (2021, March 12). In *WikiPedia*. https://en.wikipedia.org/wiki/Cracking_of_wireless_networks


### 7. Pixie-Dust Attack
#### Pixie-Dust Attack is an attack that the attacker brute-force the key of WPS so the attacker can access the network.
WPS was used to let users accessing a router easier or when users forget the router admin panel password user can use WPS to access the router to config the router. However A WPS Pin only consists of 8 digits, an attack just simply brute-forces the WPS PIN to access your router.

#### Countermeasure:

#### Disable WPS feature
* Some router may able to disable the WPS feature from the admin panel on the router. After disabling this feature pixie-Dust attack will no longer work.

#### Replace the router
* Not all the router have the ability for you to disable the feature, so you may have to buy a new router, most router models that release in the past few years and it already has remove the WPS feature from the vendor.

##### References
Thel3l. (2017). *What is Pixie dust attack on router?.* Stack Exchange. https://security.stackexchange.com/questions/149178/what-is-pixie-dust-attack-on-router


### 8. Krack Attack
#### Krack, Key Reinstallation Attacks, is a critical flaw of the WPA2 Wi-Fi encryption protocol. An attacker can exploit this flaw to read the contents of encrypted Wi-Fi traffic and serve malicious contents to the clients of the Wi-Fi network.
This vulnerability was found in 2017. A team of researchers found that the 4-way handshake design of WPA2 can let attackers re-install an encryption key easily, no matter the Wi-Fi authentication scheme is Pre-Share Key (PSK) or Extensible Authentication Protocol (EAP). This attacks fools a connected Wi-Fi client to re-install the key they are currently using. To accomplish this, a replay attack (re-sending the modified data) is needed. By capturing, forging, and replay the cryptographic information in the handshake, the attacker can decrypt the traffic with their selected key.

#### Countermeasure:

#### If provided by vendor, enable KRACK countering feature
* Some router vendors had already released the patch for KRACK, install the patch and enable the countermeasure will protect your network from KRACK.

#### Use WPA3 instead of WPA2
* WPA3 has addressed this attack already.

##### References
Vanhoef, M. (2017). *Key Reinstallation Attacks: Breaking WPA2.* https://www.krackattacks.com/
