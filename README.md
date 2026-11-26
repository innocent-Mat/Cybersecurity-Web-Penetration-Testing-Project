# Cybersecurity & Web Penetration Testing Project
## Mediroza General Hospital – Networkwalks

**Training Organization:** Networkwalks  
**Program:** Cybersecurity / Penetration Testing  
**Batch:** B083  
**Project:** Week 4 – Mediroza General Hospital  
**Target Website:** https://medirozahospital.com  
**Testing Type:** Black-Box Penetration Testing  
**Duration:** 5 Days  
**Environment:** Kali Linux

---

## 1. Project Overview

As part of my cybersecurity training with Networkwalks, I conducted a practical web penetration-testing assessment of the Mediroza General Hospital website.

The objective was to evaluate the website's security, identify potential vulnerabilities, investigate exposed services and resources, examine authentication mechanisms, and assess the protection of confidential documents.

During the assessment, I performed reconnaissance, DNS enumeration, web technology identification, HTTP analysis, WAF fingerprinting, and investigation of the hospital's patient portal.

I also identified three password-protected PDF laboratory reports within the authorized testing environment. These documents became the focus of the PDF security and password-auditing milestone.

The assessment helped me gain practical experience in web security, information gathering, vulnerability assessment, and ethical hacking.

## 2. Objectives

- Conduct reconnaissance against the target website.
- Identify domain information and DNS records.
- Identify web technologies and hosting infrastructure.
- Examine HTTP responses and security-related headers.
- Identify and understand web application security mechanisms.
- Investigate the patient portal and its document access controls.
- Examine PDF encryption and password protection.
- Learn password auditing using John the Ripper and Johnny.
- Identify potential information disclosure risks.
- Document findings and recommend security improvements.

## 3. Tools and Technologies Used

| Tool | Purpose |
|---|---|
| Kali Linux | Penetration-testing environment |
| WHOIS | Domain registration information gathering |
| DNSRecon | DNS enumeration |
| NSLookup | DNS and mail-server investigation |
| WhatWeb | Website technology fingerprinting |
| cURL | HTTP request and response inspection |
| WAFW00F | Web Application Firewall identification |
| Burp Suite | Web application traffic inspection |
| John the Ripper | Password auditing |
| Johnny GUI | Graphical interface for John the Ripper |
| pdf2john | PDF password hash extraction |
| ExifTool | File metadata analysis |
| PDFinfo | PDF document information analysis |

## 4. Practical Activities and Methodology

### 4.1 Domain Reconnaissance – WHOIS

**Tool:** WHOIS

Command:

```bash
whois medirozahospital.com
```

Purpose:
- Identify domain registration information.
- Identify the registrar.
- Examine domain registration and expiration dates.
- Identify name servers.
- Examine domain ownership information where publicly available.

**Observation:**

The WHOIS investigation identified Namecheap as the domain registrar and showed that registrant information was protected through a privacy service.

This demonstrated how publicly available domain registration information can support reconnaissance.

### 4.2 DNS Enumeration – DNSRecon

**Tool:** DNSRecon

Command:

```bash
dnsrecon -d medirozahospital.com
```

Purpose:
- Identify DNS records.
- Discover authoritative name servers.
- Examine mail exchange records.
- Identify available service records.
- Gather information about the domain's DNS infrastructure.

**Observation:**

The enumeration identified DNS information, including:

- A records.
- NS records.
- MX records.
- TXT records.
- SRV records.

The results provided information about the domain's hosting and email infrastructure.

### 4.3 DNS Investigation – NSLookup

**Tool:** NSLookup

Commands:

```bash
nslookup medirozahospital.com
```

To investigate mail servers:

```bash
nslookup -type=MX medirozahospital.com
```

Purpose:
- Resolve domain names into IP addresses.
- Identify mail exchange servers.
- Understand DNS resolution.
- Examine publicly available DNS information.

**Observation:**

The domain resolved to an IP address, and the MX lookup identified the mail exchange infrastructure.

### 4.4 Website Technology Identification – WhatWeb

**Tool:** WhatWeb

Command:

```bash
whatweb medirozahospital.com
```

Purpose:
- Identify web server technologies.
- Detect website frameworks and technologies.
- Identify HTTP-related information.
- Gather technical information about the web application.

**Observation:**

The scan identified:

- LiteSpeed Web Server.
- HTML5.
- A hosting-related IP address.
- HTTP response information.
- A redirection to the website's HTTPS version.

The results also showed HTTP 403 responses during some requests.

A 403 response indicates that access to a requested resource was forbidden. Further testing is needed to determine whether this is expected access control or a security misconfiguration.

### 4.5 HTTP Analysis – cURL

**Tool:** cURL

Commands:

```bash
curl -I https://medirozahospital.com
```

To inspect the HTTP response:

```bash
curl -i https://medirozahospital.com
```

Purpose:
- Inspect HTTP response codes.
- Examine response headers.
- Understand redirections.
- Identify server information.
- Investigate application responses.

**Observation:**

The HTTP investigation revealed information such as:

- HTTP response status.
- Content type.
- Last-modified information.
- Server identification.
- Response headers.

The observed server identification included LiteSpeed.

### 4.6 Web Application Firewall Identification – WAFW00F

**Tool:** WAFW00F

Command:

```bash
wafw00f https://medirozahospital.com
```

Purpose:
- Identify whether a website is protected by a Web Application Firewall.
- Fingerprint known WAF technologies.
- Understand the role of web traffic filtering.

**Observation:**

The tool identified LiteSpeed as the apparent WAF technology protecting the website.

This demonstrated the importance of understanding defensive technologies during penetration testing.

Note: WAF fingerprinting is an indication, not proof that all application components are adequately protected.

### 4.7 Patient Portal Investigation

During the assessment, I examined the Mediroza patient portal.

The portal contained a section titled **My Lab Reports**, which displayed three password-protected PDF laboratory reports.

The portal indicated that passwords were sent by the laboratory to patients to open their documents.

The investigation focused on:

- Understanding the portal's authentication mechanism.
- Examining document access controls.
- Identifying how laboratory reports were provided.
- Understanding PDF password protection.
- Assessing the risks associated with confidential document handling.

The screenshots show three encrypted PDF reports available in the portal.

Patient information was treated as confidential and is not reproduced in this public project documentation.

## 5. PDF Security and Password Auditing

An important part of the project involved understanding the security of password-protected PDF documents.

### John the Ripper

John the Ripper is a password security auditing tool used to test password strength and recover passwords from supported password hashes.

### Johnny GUI

Johnny provides a graphical interface for John the Ripper, making password auditing easier to manage.

### pdf2john

This utility extracts password-verification information from supported encrypted PDF documents for analysis using John the Ripper.

### Password auditing concepts studied

- PDF encryption.
- Password hashes.
- Dictionary attacks.
- Brute-force attacks.
- Wordlists.
- Password complexity.
- Password recovery.

The objective was to evaluate the strength of document password protection using authorized test files.

## 6. Security Observations and Potential Findings

The following table distinguishes what was observed from what still requires security validation.

| Observation | Security significance |
|---|---|
| Domain registration information was publicly available | Useful reconnaissance information; not automatically a vulnerability |
| DNS records were discoverable | Normal DNS functionality; configuration should be reviewed |
| LiteSpeed technology was identified | Technology fingerprinting may help attackers identify infrastructure |
| HTTP 403 responses were observed | Access restrictions were present; their effectiveness needs validation |
| Server information appeared in HTTP responses | Review whether unnecessary information disclosure can be reduced |
| Three encrypted laboratory reports appeared in the patient portal | Confidential documents require strong authentication and access controls |
| PDF files used password protection | Password strength and encryption configuration should be assessed |

### Potential Security Improvements

1. Review HTTP security headers and implement appropriate protections.
2. Keep server software and web applications updated.
3. Enforce strong authentication and authorization.
4. Ensure that patient documents cannot be accessed by unauthorized users.
5. Use strong encryption for confidential PDF documents.
6. Apply unique, sufficiently strong document passwords.
7. Avoid exposing unnecessary server and technology information.
8. Monitor access to sensitive documents.
9. Implement appropriate logging and security monitoring.
10. Conduct regular vulnerability assessments.

These are recommendations for validation and improvement, not claims that every listed weakness was confirmed.

### 4.7 Web Application Security Testing – Burp Suite

**Tool:** Burp Suite Community Edition

I used Burp Suite to inspect and analyze HTTP traffic between the browser and the Mediroza web application.

Activities included:

- Intercepting and examining HTTP requests and responses.
- Investigating login and authentication mechanisms.
- Inspecting URL parameters and form inputs.
- Examining how the application processes user input.
- Testing for potential input-validation vulnerabilities.
- Analyzing application responses during security testing.

### 4.8 SQL Injection (SQLi) Testing

**Tools:** Burp Suite, Browser Developer Tools, and other supporting web security tools.

I conducted SQL Injection security testing to assess whether the website's input fields and application parameters were properly protected against malicious SQL queries.

Areas investigated included:

- Login and authentication forms.
- User input fields.
- URL parameters.
- Database-driven application responses.
- Input validation and error handling.

**SQL Injection (SQLi)** is a web application vulnerability that occurs when an application improperly handles user input in database queries. An attacker may exploit this weakness to manipulate database operations or access information without authorization.

The assessment focused on understanding whether the application was vulnerable to SQL injection and evaluating the potential security impact.

**Recommended security measures:**

1. Use parameterized SQL queries and prepared statements.
2. Implement server-side input validation.
3. Apply the principle of least privilege to database accounts.
4. Avoid displaying detailed database errors to users.
5. Regularly conduct SQL injection security assessments.

### 4.9 Additional Web Security Testing Tools

| Tool | Application |
|---|---|
| Burp Suite | HTTP interception and web application testing |
| SQLMap | Automated SQL injection testing in authorized environments |
| Nmap | Network and service discovery |
| Gobuster | Directory and resource discovery |
| WhatWeb | Website technology identification |
| WAFW00F | WAF fingerprinting |
| cURL | HTTP request and response analysis |

**Important:** SQL Injection testing was part of the assessment methodology. A successful SQL injection vulnerability should only be reported as confirmed when supported by reproducible evidence.

### Additional Skills Acquired

- SQL Injection identification and assessment.
- Web application security testing.
- HTTP request manipulation.
- Authentication security assessment.
- Database security fundamentals.
- Input validation and sanitization.
- Burp Suite Proxy and HTTP traffic analysis.
- Understanding OWASP Top 10 vulnerabilities.



## 10. Project Milestones

### M1 – Initial Access
- Reconnaissance.
- DNS enumeration.
- Website technology identification.
- Web application investigation.
- Patient portal assessment.
- Identification of three PDF reports.

### M2 – Data Extraction and PDF Security
- PDF encryption analysis.
- Password hash extraction.
- John the Ripper.
- Johnny GUI.
- Wordlist-based password auditing.
- Verification of authorized test documents.

### M3 – Further Data Exposure Analysis
- File metadata investigation.
- Analysis of authorized assessment evidence.
- Investigation of potential sensitive information exposure.
- Documentation of security implications.

### M4 – Penetration Testing Report
- Executive summary.
- Scope and methodology.
- Security findings.
- Supporting evidence.
- Risk assessment.
- Recommendations and remediation.

## 11. Skills and Knowledge Acquired

Through this hands-on project, I developed practical knowledge and experience in:

**Cybersecurity Fundamentals**
- Ethical hacking.
- Penetration-testing methodology.
- Black-box security assessment.
- Information security.
- Vulnerability assessment.

**Network and Web Security**
- DNS enumeration.
- Domain reconnaissance.
- HTTP protocol analysis.
- Web technology fingerprinting.
- WAF identification.
- Web application security.

**Password and Document Security**
- PDF encryption.
- Password auditing.
- John the Ripper.
- Johnny GUI.
- Dictionary and brute-force attacks.
- File metadata analysis.

**Security Assessment and Reporting**
- Evidence collection.
- Vulnerability documentation.
- Risk identification.
- Security recommendations.
- Professional penetration-testing reports.

## 12. Evidence and Screenshots

The following screenshots document my practical activities:

| Evidence | Description |
|---|---|
| 01 | Mediroza patient portal and laboratory reports |
| 02 | WHOIS domain reconnaissance |
| 03 | WHOIS registration information |
| 04 | WhatWeb technology identification |
| 05 | DNSRecon enumeration |
| 06 | NSLookup and MX record investigation |
| 07 | WAFW00F fingerprinting |
| 08 | Pathology report document examination |
| 09 | Additional laboratory report examination |
| 10 | HTTP and web application investigation |

<img width="1734" height="829" alt="Screenshot_2026-11-24_08-48-07" src="https://github.com/user-attachments/assets/33e67d70-9542-417e-877a-8eb532408b31" />
<img width="1613" height="955" alt="Screenshot_2026-11-24_08-48-49" src="https://github.com/user-attachments/assets/a608265c-7867-453b-927d-8543b56880ed" />
<img width="748" height="715" alt="Screenshot_2026-11-24_09-12-55" src="https://github.com/user-attachments/assets/dbc88fde-2371-4599-ad67-c9c96f9878c0" />
<img width="1092" height="815" alt="Screenshot_2026-11-24_09-13-20" src="https://github.com/user-attachments/assets/f512937b-1cc5-4d77-9e3e-abdfd8765982" />
<img width="1283" height="790" alt="Screenshot_2026-11-24_09-14-09" src="https://github.com/user-attachments/assets/2a92bc6a-fbcb-45dc-b92b-ecdbfcd5ba80" />
<img width="1624" height="881" alt="Screenshot_2026-11-24_09-13-39" src="https://github.com/user-attachments/assets/55fb784e-cc11-4951-8a62-e86cbe1caf90" />
<img width="1270" height="710" alt="Screenshot_2026-11-24_09-16-28" src="https://github.com/user-attachments/assets/b42fceaa-a016-4d9f-b74c-11b39742ed5a" />
<img width="859" height="390" alt="Screenshot_2026-11-24_09-17-12" src="https://github.com/user-attachments/assets/a308dc2f-1f5f-4b36-a8e2-53a80a6d375b" />
<img width="671" height="896" alt="Screenshot_2026-11-26_02-44-35" src="https://github.com/user-attachments/assets/19fa4191-e0fe-4ba3-a509-d0d9eb78ff21" />
<img width="789" height="892" alt="Screenshot_2026-11-26_02-46-32" src="https://github.com/user-attachments/assets/16c544e6-8884-44f7-b13a-2897cd0d5c8d" />



Screenshots are maintained as supporting evidence for the assessment. Confidential patient information should be redacted before public sharing.

## 13. Ethical and Legal Considerations

The assessment was conducted as part of the authorized Networkwalks training project.

Testing activities must remain within the approved scope.

No unauthorized access, disclosure, modification, or distribution of patient information is permitted.

All sensitive information must be handled responsibly and protected in accordance with applicable privacy and security requirements.

## 14. Conclusion

This project provided practical exposure to cybersecurity and web penetration testing.

By assessing the Mediroza General Hospital website, I gained experience in reconnaissance, DNS enumeration, web technology identification, HTTP analysis, WAF fingerprinting, patient portal investigation, and PDF document security.

The assessment also helped me understand the importance of secure authentication, access control, encryption, and confidential data protection, particularly in healthcare environments.

**This experience strengthened my practical cybersecurity skills and my interest in ethical hacking, penetration testing, network security, and application security.**

---

**Project:** Mediroza General Hospital Penetration Testing  
**Organization:** Networkwalks  
**Batch:** B083  
**Field:** Cybersecurity and Ethical Hacking
