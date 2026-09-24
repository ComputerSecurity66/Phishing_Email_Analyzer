# 🔐 Phishing Email Analyzer

> **PROPRIETARY SOFTWARE — NOT OPEN SOURCE**
> Copyright © 2026 VALOR. All Rights Reserved.

A Windows-based **C# cybersecurity assessment and phishing-analysis utility** designed to help security professionals, technicians, researchers, and authorized users investigate suspicious email messages, URLs, attachments, and sender authentication information.

The application provides a command-line interface for performing several defensive security-analysis tasks without automatically exposing API credentials in the source code.

---

## 🛡️ Features

### 1. Extract URLs from `.eml` Files

Extracts HTTP and HTTPS URLs from email message files.

Useful for:

* Investigating suspicious emails
* Identifying links contained in messages
* Collecting URLs for further security analysis
* Supporting manual phishing investigations

> URL extraction is a text-based analysis function and does not replace a full MIME email parser.

---

### 2. SHA-256 File Hashing

Calculates the SHA-256 hash of a selected file.

Useful for:

* Malware-analysis workflows
* File identification
* IOC collection
* Comparing files against known hashes
* Security documentation

The selected file is hashed locally and is not automatically uploaded by this function.

---

### 3. VirusTotal URL Analysis

Allows a user to submit a URL to VirusTotal and retrieve the resulting analysis information using a user-provided API key.

This can help with:

* Suspicious website investigation
* Phishing URL analysis
* Security intelligence collection
* Detection-result review

A VirusTotal API key must be configured by the user.

> VirusTotal is a third-party service. Its API availability, limits, and permitted uses are controlled by VirusTotal's own terms and policies.

---

### 4. URL Sandboxing and Threat Intelligence Checks

The application can perform multiple checks against a submitted URL, including:

* URLhaus
* PhishTank
* HTTPS/TLS certificate assessment

The program separates **malicious**, **clean/not found**, and **unavailable/error** results so that a failed external service is not incorrectly reported as a clean URL.

> Third-party threat-intelligence results should be treated as supporting evidence rather than absolute proof.

---

### 5. Email Sender & Authentication Assessment

Analyzes `.eml` headers for security-relevant information such as:

* Sender email address
* Sender display name
* Received IP information
* SPF results
* DKIM signature presence
* DMARC authentication results
* Authentication-Results headers

The feature is intended to support investigation of suspicious email messages.

> Presence of a DKIM signature or an authentication header alone does not prove that an email is legitimate. Email authentication results should be interpreted together with the complete message headers and other evidence.

---

## 🔑 API Key Management

The application provides an API Management menu for:

* Setting VirusTotal API keys
* Setting URLhaus Auth-Keys
* Setting PhishTank API keys
* Clearing individual keys
* Clearing all configured keys
* Viewing API configuration status

API credentials are protected using Windows **Data Protection API (DPAPI)** with the current Windows user scope.

Credentials are stored in the user's application-data directory rather than being hard-coded into the GitHub source code.

---

## 📁 Local Data Locations

API credentials are stored under:

```text
%APPDATA%\PhishingAnalyzer\
```

Example files:

```text
apikey.txt
urlhaus_key.txt
phishtank_key.txt
```

These files contain protected credential data rather than plain-text API keys.

Do not copy these credential files into the GitHub repository.

---

## 💻 System Requirements

* Windows 10 or later
* Windows 11 recommended
* .NET 8
* Internet connection for external threat-intelligence services
* API credentials for services that require authentication

---

## 🚀 Build the Project

Clone or download the repository and open the project in Visual Studio.

Restore dependencies:

```powershell
dotnet restore
```

Build:

```powershell
dotnet build -c Release
```

Publish as a Windows executable:

```powershell
dotnet publish -c Release -r win-x64 --self-contained true -p:PublishSingleFile=true -p:IncludeNativeLibrariesForSelfExtract=true -o publish
```

---

## 🧪 Typical Workflow

A typical defensive investigation can follow this process:

```text
Suspicious Email
       │
       ▼
Extract URLs
       │
       ├──► VirusTotal
       │
       ├──► URLhaus
       │
       └──► PhishTank
       │
       ▼
Review Email Headers
       │
       ├──► SPF
       ├──► DKIM
       └──► DMARC
       │
       ▼
Hash Suspicious Attachment
       │
       ▼
Document Security Findings
```

---

## ⚠️ Security and Safety Notes

This application is designed for **defensive cybersecurity analysis**.

Use it only for:

* Systems you own
* Systems you are authorized to analyze
* Security research conducted within applicable policies
* Incident-response and investigation activities
* Educational and laboratory environments

Do not use the application to access, test, or investigate systems without appropriate authorization.

---

## 🔒 Third-Party Services

This project may integrate with external services including:

* VirusTotal
* URLhaus
* PhishTank

These services are **independent third-party services** and are not owned by this project.

Their availability, API requirements, rate limits, data handling, and licensing or usage restrictions are controlled by their respective providers.

Users are responsible for obtaining and using API credentials in accordance with the providers' current terms and policies.

---

# 📩 Source Code Modification & Development Requests

## Want to Modify or Develop This Project?

If you would like to **modify the source code, develop new features, extend the application, create integrations, build plugins, improve existing functionality, or continue development of this project, please contact me first.**

I am open to discussing:

* Authorized source-code modifications
* New feature development
* Security-analysis improvements
* Collaboration
* Integrations
* Extensions
* Custom development
* Licensing arrangements

**Written permission must be obtained before modifying, redistributing, publishing, commercially using, or creating derivative works from the source code.**

> 🔒 **This repository is publicly accessible on GitHub, but the software remains proprietary. Public access does not mean that the source code has been released under an open-source license.**

Please contact the copyright holder to discuss permission for source-code modification, development, redistribution, commercial use, or other authorized projects.

---

# 🚫 Proprietary Software Notice

**Phishing Email Analyzer** is proprietary software developed by **VALOR**.

Copyright © 2026 VALOR. All Rights Reserved.

This project is **not open-source software** and is **not licensed under MIT, Apache-2.0, GPL, LGPL, BSD, or another open-source license**.

Unless explicitly authorized in writing by the copyright holder, you may not:

* Copy the source code
* Modify the source code
* Create derivative works
* Redistribute the source code
* Repackage the software
* Sell the software
* Publish modified versions
* Integrate the source code into another product
* Sublicense the software
* Remove copyright notices
* Re-license the project
* Convert the project into an open-source project
* Release modified versions under an open-source license

All rights not expressly granted are reserved by the copyright holder.

See the `LICENSE` file for the complete proprietary licensing terms.

---

# 🤝 Contributions

Because this is a proprietary project, contributions are not automatically authorized.

Anyone interested in contributing or developing the application should **contact the copyright holder before making or distributing modifications**.

Potential areas for authorized development include:

* Phishing detection improvements
* Email parsing improvements
* URL analysis
* Threat-intelligence integrations
* Security reporting
* Detection enhancements
* Performance improvements
* Windows compatibility
* User-interface improvements
* Security research features

Any accepted contribution remains subject to the project's proprietary licensing requirements and any additional agreement provided by the copyright holder.

---

# 📋 Limitations

This application is an **assessment and investigation utility**.

It should not be considered:

* A replacement for Microsoft Defender
* A replacement for enterprise EDR/XDR
* A replacement for email security gateways
* A replacement for professional malware-analysis environments
* A guarantee that a URL or email is safe
* A guarantee that a URL or email is malicious

Threat-intelligence databases may contain incomplete, delayed, incorrect, or changing information.

A result of **CLEAN** or **NOT FOUND** means that the configured service did not report the submitted indicator as malicious at the time of the check. It does not guarantee that the indicator is safe.

An **UNAVAILABLE** result means the application could not successfully obtain a reliable result from the external service.

---

# 📜 License

This project is distributed under a **proprietary license**.

Copyright © 2026 VALOR. All Rights Reserved.

No open-source license is granted.

Commercial use, redistribution, modification, derivative development, integration, or other use outside the permissions of the proprietary license requires written authorization from the copyright holder.

---

# 👤 Project

**Project Name:** Phishing Email Analyzer
**Developer:** VALOR
**Year:** 2026
**Platform:** Windows
**Language:** C# / .NET 8

---

## 🔐 Copyright

Copyright © 2026 VALOR. All Rights Reserved.

**Phishing Email Analyzer is proprietary software and is not open source.**
