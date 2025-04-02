---
title: "Hacking in Belgium is legal"
date: 2025-04-02 01:00:00 +0200
categories:
  Tutorials
  Practical
tags:
  how-to
  ccb
pin: true
mermaid: true
image:
  path: /Excis3/excis3.github.io/main/media/ccb.png
---

For just over two years now, it's been legally permitted to conduct security research on digital assets **located in Belgium**.
This is a huge step forward for the ethical hacking community and an exciting opportunity for professionals like myself. As a Belgian citizen and security researcher, this opens up new avenues for contributing to a safer digital landscape.

In this post, I’ll walk you through the essentials:
1. **What’s allowed**
2. **What’s off-limits**
3. **And how to report vulnerabilities the right way**


## Rules of the game

![logo-ccb.svg](https://raw.githubusercontent.com/Excis3/excis3.github.io/refs/heads/main/media/logo_ccb.svg)

The Centre for Cybersecurity Belgium (**CCB**) has published an official [framework for vulnerability disclosure](https://ccb.belgium.be/cert/vulnerability-reporting-ccb). It enables responsible researchers to investigate vulnerabilities on Belgian systems within legal boundaries.

> **In Short:** You can legally hack on networks and information systems located in Belgium, but only if you stick to the rules.
{: .prompt-info }


Before diving in, make sure you understand the legal and ethical expectations. Here's a breakdown of the core principles:
* **Stay proportional:** Act only to the extent necessary to verify the vulnerability and report it. No deeper digging than required.
* **Be ethical:** Your actions must be free of malicious intent or personal gain.
* **Notify quickly:** Send a full report within 72 hours.
* **Don’t go public without permission:** Public disclosure is only allowed with CCB approval, which will also consider the position of the affected organization.
* **Some targets require prior consent:** If you're targeting certain organizations (such as judicial bodies or specific governmental services), you must first sign a written agreement before starting your research.


Even with legal permission, some activities are strictly off-limits:
* **Installing malware**
* **Performing DDoS attacks**
* **Social engineering or phishing**
* **Spamming**
* **Password theft or brute force attempts**
* **Deleting data**
* **Damaging or altering systems or data**


## How to report

![report.jpg](https://raw.githubusercontent.com/Excis3/excis3.github.io/refs/heads/main/media/report.jpg)

So, you’ve discovered a potential vulnerability, great job! Now comes the important part: responsibly reporting it.
Before jumping into emails and forms, let’s first determine the correct reporting path. Here’s a step-by-step guide to make sure your report is both effective and compliant with the **Belgian legal framework**.

### Steps to follow:

**Step 1: Check for a Vulnerability Disclosure Program**

Start by verifying if the target organization has a vulnerability disclosure policy in place.
A good first stop is to check if the domain has a security.txt file. This file typically contains instructions on how to report vulnerabilities securely.

> **You can usually find it at:** https://www.domain.be/.well-known/security.txt
{: .prompt-info }

If that file doesn't exist, look for a “Security,” “Legal,” or “Contact” page on the site for any reporting channels (e.g., email address, contact form, or ticketing system).


**Step 2: Contact the Asset Owner**

Once you've identified the correct channel, send your initial disclosure to the asset owner. This should happen within 72 hours of discovering the vulnerability (ideally even sooner—remember).


**Mail template to asset owner:**
```
Subject: Responsible Disclosure – [Short Title of Vulnerability]

Hello [Organization Name] team,

I am a security researcher, and I have identified a potential vulnerability affecting your digital assets. I am contacting you in good faith as part of a responsible disclosure process.

Brief Summary:
- Affected Asset: [URL/IP/Service]
- Type of Vulnerability: [e.g., XSS, IDOR, SQL Injection]
- Date Discovered: [DD/MM/YYYY]
- Potential Impact: [e.g., data leakage, privilege escalation]

I am happy to share a detailed report and assist further if needed. I will also be reporting this issue to the Centre for Cybersecurity Belgium (CCB) as per the legal framework for ethical hacking.

Best regards,  
[Your Name / Alias]  
[Optional: PGP Key, Twitter, LinkedIn, etc.]
```

**Report Template to asset owner:**
Convert to a PDF and include in the mail.
```
Title: Responsible Disclosure Report – [Vulnerability Name]

Researcher Information:
- Name or Alias: [Your Name]
- Contact Email: [Your Email]


Vulnerability Details:
- Affected System(s): [URLs, IPs, domains]
- Type of Vulnerability: [e.g., SQLi, SSRF, etc.]
- Date of Discovery: [DD/MM/YYYY]
- Steps to Reproduce: [Detailed steps or PoC]
- Potential Impact: [Risk level and possible exploitation]
- Recommendations: [How to fix or mitigate]

Legal Notice:
This report is shared in compliance with the Belgian legal framework for ethical hacking and without malicious intent.
```


**Step 3: Notify the CCB**

Once the organization has been contacted, it’s time to alert the Centre for Cybersecurity Belgium (CCB).

How to Notify the CCB:
 - Download and complete the official reporting form:
   - [CVDP_Notification_form.docx](https://ccb.belgium.be/sites/default/files/2024-12/CVDP%20Procedure%20Complete%20Notification%20form%20EN.docx)
   - [CVDP_Notification_form.pdf](https://ccb.belgium.be/sites/default/files/2024-12/CVDP%20Procedure%20Complete%20Notification%20form%20EN.pdf)
 - Save the completed form in a password-protected ZIP file (Max size: 7 MB). This helps bypass email antivirus scanners.
 - Email the ZIP file to:
   `vulnerabilityreport[at]ccb.belgium.be`
 - Include the password in the body of the email.

After sending your mail to the asset owner, you can also create a report to the CCB in the following way:

**Report mail to CCB:**
```
Subject: Responsible Disclosure – [Vulnerability Name]

Hello CCB team,

Attached you’ll find the completed notification form regarding a potential vulnerability I discovered on a Belgian asset.

The report is in a password-protected ZIP file:
- ZIP Password: [YourPassword123!]

This vulnerability has also been disclosed to the affected organization.

Please feel free to contact me for additional information.

Kind regards,  
[Your Name / Alias]  
[Optional: PGP key or other contact info]
```

**(Optional) Encrypting with PGP**

The CCB previously recommended encrypting your report with PGP, though this is reportedly no longer mandatory. Still, if you prefer an extra layer of security you can find the public key at the official page: [CCB sending secure messages](https://ccb.belgium.be/cert/send-encrypted-message). There you can download the PGP key you need to encrypt your mail.


## Conclusion

Belgium is leading by example in enabling ethical hacking under a responsible framework. This is a fantastic opportunity to contribute to cybersecurity in a legal and constructive way.
If you’re planning to explore this domain, I highly recommend checking out the [official guidelines by the CCB](https://ccb.belgium.be/cert/vulnerability-reporting-ccb)and ensuring you’re fully compliant.

Stay curious, stay ethical.

**Excis3**
