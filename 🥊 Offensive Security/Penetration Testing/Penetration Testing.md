# Penetration Testing

A common penetration test consists of the following stages:

## 1. Defining the Scope
The penetration test engagement scope outlines the IP ranges, hosts, and applications to be tested, differentiating them from out-of-scope items.
## 2. Gathering Information
Once the scope and timeline are agreed upon with the client, the information gathering phase begins, aiming to amass as much data about the target as possible.

Reconnaissance is usually performed during this stage to collect details about the target organization's infrastructure, assets, and personnel. This can be passive or active. 

Passive methods minimize direct interaction, while active methods directly probe the infrastructure. As active information gathering leaves a larger footprint, passive gathering is often favored to reduce exposure.

>> Remember that information gathering (or enumeration) extends beyond initial reconnaissance. As the penetration test unfolds, we'll continue gathering data while gaining access and moving laterally, ultimately expanding our knowledge of the target's attack surface.

## 3. Detecting Vulnerabilities
4. Gaining Initial Access
5. Escalating Privileges
6. Moving Laterally
7. Reporting and Analysis
8. Learning from Experience and Applying Remediation








Types of Testing
- [[Black-box testing]]: The tester has no prior knowledge of the target system or its infrastructure. They must discover vulnerabilities by probing the system as an external attacker would.
- [[White-box testing]]: The tester has full knowledge of the target system, including source code, architecture, and documentation. This allows for a more in-depth analysis of potential vulnerabilities.
- [[Gray-box testing]]: The tester has partial knowledge of the system, usually limited to user-level access. This approach combines elements of both black-box and white-box testing.

- [[Internal testing]]: This type of testing simulates attacks from within the organization, often focusing on insider threats or compromised internal accounts.
- [[External testing]]: This testing targets an organization's externally facing infrastructure, such as websites, email servers, and firewalls, to assess security from an outsider's perspective.

- [[Blind testing]]: The tester is given minimal information about the target system and must gather intelligence before attempting to exploit vulnerabilities.
- [[Double-blind testing]]: Both the tester and the organization's security team have limited knowledge of the test. This simulates a real attack scenario and tests the effectiveness of the organization's incident response and detection capabilities.

- [[Targeted testing]]: This type of testing focuses on specific parts of the system or specific vulnerabilities, often as a follow-up to a broader penetration test.

- [[Red team testing]]: A group of security professionals, known as the "red team," attempt to breach the organization's security while the organization's security team, or "blue team," tries to defend against the simulated attack.



- [[Social engineering testing]]: This testing focuses on exploiting the human element of an organization by manipulating employees into divulging sensitive information or performing actions that compromise security.


- [[Wireless network testing]]: This type of penetration testing focuses on identifying and exploiting vulnerabilities in wireless networks, such as Wi-Fi access points and devices.

- [[Physical security testing]]: This testing involves assessing the physical security measures in place at a facility, such as access controls, surveillance systems, and locks, to identify potential weaknesses that could be exploited.

- [[Web application testing]]: This type of testing focuses specifically on web-based applications, evaluating their security against attacks such as SQL injection, cross-site scripting (XSS), and authentication bypass.

- [[Mobile application testing]]: This testing assesses the security of mobile applications on various platforms, such as Android and iOS, to identify potential vulnerabilities and weaknesses.

- [[Cloud environment testing]]: This type of testing focuses on assessing the security of cloud-based infrastructure, including the configuration of virtual machines, containers, and storage, as well as access controls and compliance with relevant security standards.
