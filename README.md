# Task 3 : Perform a Basic Vulnerability Scan on Your PC

## Objective

The purpose of this task was to perform a vulnerability assessment on the local machine ('localhost') using **Tenable Nessus**. This was done to identify potential weaknesses and misconfigurations that could be exploited in a real-world scenario.

---

## Tools Used 

- **Tenable Nussus** (Community Edition) : Vulnerability scanner
- **Localhost Target**                   : Machine used for scanning
- **Port 445, HTTPS, SMB, and HTTP**     : Monitored services

---

## Scan Overview

- **Scan Policy** : Basic Network Scan
- **Target** : 127.0.0.1 (localhost)
- **Start Time** : 1:02 PM
- **End Time** : 1:10 PM
- **Duration** : ~8 minutes
- **Scanner** : Local Scanner
- **Serverity Base** : CVSS v3.0

A total of **23 vulnerabilites** were detected across multiple categories and severities.

---

## Vulnerability Summary

| Serverity | | Count |
| --------- | | ----- |
| Critical  | | 0     |
| High      | | 0     |
| Medium    | | 2     |
| Low       | | 0     |
| Info      | | 21    |

--- 

## Notable Vulnerabilites 

### 1. **SMB Signing Not Required** 
- **Serverity**   : Medium 
- **Plugin ID**   : 57608 
- **Port**        : 445/tcp (CIFS/SMB)
- **Description** : 
    The remote SMB server does not enforce message signing. This allow attackers to potentially carry out. **man-in-the-middle (MITM)** attacks.
- **Remediation** : 
    Enforce message signing in the server's configuration :
        - Windows : 
            Enable 'Microsoft network server : 
                Digitally sign communications (always)'
        - Linux/Samba : 
            Set 'server signing = mandatory'

--- 

### 2. **SSL Certificate Cannot Be Trusted** 
- **Serverity**   : Medium 
- **CVSS**        : 6.5 
- **Description** : 
    The SSL certificate presented by the server cannot be verified by a trusted certificate authority. 
- **Impact**      : 
    Clients may refuse connections, or attackers could impersonate the server.
- **Solution**    : 
    Replace the self-signed certificate with a valid one issued by a trusted CA.

---

## Information Findings 

These are not direct vulnerabilites, but they provide useful context :

- **SSL Certificate Information** 
- **SSL Cipher Suites Supported** 
- **SSL Perfect Forward Secrecy Cipher Suites Supported** 
- **HTTP Server Type and Version** 
- **HTTP Protocol Information**

These findings reveal server behavior, supported cryptography, and software versions - which can be useful during reconnaissance in a real attack.

--- 

## Screenshots

The following screenshots were captured during the assessment and can be found in the 'screenshots/' folder :

1. 'SMB_Signing.png' - Vulnerability details of SMB signing issue
2. 'SSL_Issues.png' - Overview of SSL-related medium and info vulnerabilites 
3. 'HTTP_Info.png' - Information insights about the web server 

--- 

## Insights and Reflection 

This scan highlights that even a **localhost** setup can contain **non-trivial misconfigurations** that need attention, especialy when preparing a machine for deployment or development. While no critical vulnerabilites were found, the **SMB and SSL issues** are worth resolving, especially in enterprise or internet-facing enviroments. 

As an intern, this task helped me understand how to : 
- Interpret Nessus results beyound just severity levels 
- Differentiate between exploitable and informational findings 
- Recommend actionable, system-specific remediations 

--- 

## Recommendation 

- **Fix SMB Signing Misconfiguration** 
- **Install a valid SSL certificate from a trusted CA** 
- **Harden cipher suites and improve TLS settings** 
- **Continue periodic scanning to catch new vulnerabilites** 

## Conclusion 

This scan was successful, and all findings were documented with evidence. The task provided practical exposure to the vulnerability assessment process, allowing hands-on experience in interpreting and responding to real vulnerabilities on a local machine.