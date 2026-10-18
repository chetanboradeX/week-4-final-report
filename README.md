# 🔐 Black-Box Penetration Testing Report

### Mediroza General Hospital | NETWORKWALKS | Week 04 | Batch B083

<p align="center">
  <img src="https://img.shields.io/badge/Project-Black--Box%20Pentesting-red?style=for-the-badge" alt="Black Box Penetration Testing">
  <img src="https://img.shields.io/badge/Platform-Kali%20Linux-blue?style=for-the-badge&logo=kalilinux" alt="Kali Linux">
  <img src="https://img.shields.io/badge/Focus-Web%20Application%20Security-orange?style=for-the-badge" alt="Web Application Security">
  <img src="https://img.shields.io/badge/Batch-B083-green?style=for-the-badge" alt="Batch B083">
</p>

---

## 📌 Project Overview

This project focuses on **Black-Box Penetration Testing and Vulnerability Assessment** of a healthcare web application as part of the NETWORKWALKS Cybersecurity Internship Program.

Black-box penetration testing is a security assessment method in which a tester evaluates an application from an external perspective without being provided with its internal source code or complete system architecture.

The assessment covered reconnaissance, attack-surface discovery, authentication testing, document security assessment, metadata inspection, sensitive-data exposure analysis, risk assessment, and remediation planning.

The project demonstrates how multiple security weaknesses can combine to increase the risk to an organization's confidential information.

> **Important:** This public README summarizes the training assessment. The target's exact address, sensitive records, recovered passwords, and precise locations of exposed resources are intentionally excluded.

---

## 🎯 Project Objectives

The main objectives of this project were:

- Perform passive and active reconnaissance.
- Identify externally visible services and technologies.
- Enumerate discoverable web paths and application resources.
- Assess authentication handling and unsafe input processing.
- Evaluate access controls protecting patient reports.
- Examine password protection applied to PDF documents.
- Perform authorized offline password recovery for the supplied training files.
- Inspect document metadata for unintended information disclosure.
- Assess the exposure of database backups and sensitive records.
- Classify identified findings according to their risk.
- Recommend practical remediation measures.
- Prepare a professional penetration-testing report.

---

## 📋 Project Information

| Field | Details |
|---|---|
| Project Title | Black-Box Penetration Testing |
| Client / Target | Mediroza General Hospital |
| Program | NETWORKWALKS Cybersecurity Internship |
| Batch | B083 |
| Project Week | Week 04 |
| Engagement Type | Full Black-Box Penetration Test and Vulnerability Assessment |
| Testing Approach | External security assessment |
| Primary Focus | Web Application Security |
| Environment | Authorized training assessment |
| Report Prepared By | CHETAN BORADE|
| Overall Risk Rating | Critical, as assessed in the supplied report |

---

## ✅ Authorization and Scope

The supplied report records written authorization for the assessment through NETWORKWALKS.

The assessment covered the agreed target and the following major modules:

- **M1 — Initial Access**
- **M2 — Data Extraction and Password Cracking**
- **M3 — Critical Data Exposure**
- **M4 — Penetration Testing Report**

The assessment was organized into four main phases:

1. Reconnaissance and Initial Access
2. Data Extraction and Password Cracking
3. Post-Exploitation and Sensitive Data Exposure
4. Reporting and Remediation

Testing was limited to the authorized scope. Social engineering, denial-of-service testing, and activity outside the approved scope were excluded.

---

## 🛠️ Tools and Technologies Used

The supplied report documents the following tools and technologies.

| Tool | Purpose |
|---|---|
| WHOIS | Domain-registration reconnaissance |
| nslookup | DNS resolution and target IP identification |
| cURL | HTTP response and web-server inspection |
| Gobuster | Web-directory and path enumeration |
| WAF Fingerprinting Tool | Web application firewall and server fingerprinting |
| SQL Injection Testing | Assessment of unsafe input handling and authentication behavior |
| NETWORKWALKS Hash Calculator | Generate hashes for password-protected PDF files |
| NETWORKWALKS Password Cracker | Authorized offline password recovery |
| ExifTool | Inspect document metadata |
| Database / SQL Review | Examine the supplied backup evidence and identify sensitive data categories |

*The tools listed above are based on the supplied project report. The public README does not include target-specific exploitation commands or recovered credentials.*

---

## 🔍 Phase 1: Reconnaissance and Attack-Surface Discovery

Reconnaissance was performed to understand the target's externally visible infrastructure and identify potential entry points.

### 1. WHOIS Reconnaissance

WHOIS was used to review domain-registration information and identify the registration provider and DNS nameservers.

**Objective:** Gather publicly available information about the target domain.

### 2. DNS Resolution

The `nslookup` utility was used to resolve the target domain and identify its associated IP address.

**Objective:** Understand the domain's DNS configuration.

### 3. HTTP and Web-Server Inspection

cURL was used to inspect HTTP responses and server-related headers.

The supplied evidence recorded an HTTP `403 Forbidden` response and identified LiteSpeed in the server response.

**Objective:** Examine the web server's externally visible response behavior and identify useful configuration information.

### 4. Web-Path Enumeration

Gobuster was used to enumerate discoverable directories and web resources.

The supplied report records several discoverable application and service paths. The findings helped expand the understanding of the target's attack surface and contributed to the subsequent investigation.

**Objective:** Identify accessible resources that may require additional security review.

### 5. WAF and Server Fingerprinting

A fingerprinting tool was used to examine the web application's server environment.

The supplied evidence identified the application as being hosted on a LiteSpeed-based web server.

**Objective:** Gather information about the externally visible hosting environment.

---

## 🔐 Phase 2: Initial Access and Authentication Testing

The next phase examined the patient portal's authentication behavior and handling of user-controlled input.

### SQL Injection Assessment

The supplied evidence showed a MySQLi SQL syntax error returned by the application during login testing.

This indicates that user-controlled input reached backend SQL processing without being handled safely.

The report also records successful access to the restricted patient-report area during the authorized exercise.

### Key Observation

Unsafe SQL input handling, combined with insufficient authentication enforcement, created a path to restricted application resources.

### Security Impact

Potential consequences include:

- Unauthorized access to protected application functions.
- Compromise of authentication controls.
- Exposure of confidential patient documents.
- Increased risk to patient privacy and organizational confidentiality.

### Recommended Mitigation

- Use parameterized SQL queries and prepared statements.
- Avoid constructing SQL queries by directly concatenating user input.
- Enforce authentication and authorization on the server.
- Return generic error messages to users.
- Prevent database errors and internal implementation details from being disclosed.
- Conduct security regression testing after remediation.

---

## 📄 Phase 3: PDF Document Security Assessment

The supplied evidence showed three password-protected pathology reports accessible through the restricted patient-report area.

The assessment examined the password protection applied to these files.

### 1. PDF Hash Generation

The NETWORKWALKS Hash Calculator was used to generate password-auditing hashes for the three supplied PDF files.

### 2. Authorized Password Recovery

The supplied password-cracker evidence recorded successful offline password recovery for all three documents.

The recovered passwords are not reproduced in this README.

### 3. Decrypted Document Review

According to the supplied evidence, the recovered files contained confidential pathology information, including patient identifiers, reporting details, and laboratory results.

### Key Observation

The document protection was not strong enough to prevent the demonstrated password-recovery process.

### Security Impact

Weak document passwords can expose confidential files if the documents are obtained by an unauthorized party.

### Recommended Mitigation

- Avoid relying on weak or shared document passwords.
- Use strong, randomly generated document passwords when password protection is necessary.
- Prefer authenticated storage with encryption at rest and access logging.
- Restrict access to patient reports according to patient identity and authorization.
- Review how documents are generated, distributed, and stored.
- Avoid exposing protected documents through publicly accessible resources.

---

## 🗂️ Phase 4: Document Metadata Analysis

ExifTool was used to examine metadata in a decrypted PDF report.

The supplied report records that the metadata contained document-author information, creator or producer details, and an internal comment referring to a legacy database-backup location.

This information provided an additional lead during the assessment.

### Key Observation

Internal comments and document metadata can unintentionally disclose operational information about an organization's systems.

### Security Impact

Metadata disclosure may help an attacker understand internal processes, identify legacy resources, or discover information that should not be publicly accessible.

### Recommended Mitigation

- Remove internal comments and unnecessary metadata before publishing documents.
- Review author, creator, producer, and related metadata fields.
- Automate metadata sanitization during document generation.
- Review document publishing workflows.
- Ensure sensitive internal resources are protected independently of metadata controls.

---

## 🗄️ Phase 5: Sensitive Database Backup Exposure

The supplied report documents the discovery and examination of a legacy database backup associated with the healthcare application.

The evidence identified staff and shareholder information in the backup.

The public version of this README intentionally excludes the exact backup filename, server location, and sensitive records.

### 1. Staff and Payroll Information

According to the supplied evidence, the backup contained **29 visible employee records**.

The recorded field categories included:

- Employee names.
- Job titles and departments.
- Email addresses and phone numbers.
- National identification numbers.
- Monthly salary information.
- Joining dates.

The report recorded visible monthly salary values ranging from **ZAR 19,000 to ZAR 160,000**.

### 2. Shareholder Information

The supplied evidence showed **10 shareholder records**.

The recorded information included:

- Shareholder names.
- Share percentages.
- Number of shares held.
- Share classes, including Ordinary and Preferential.

### Key Observation

The exposed backup contained information extending beyond the initial patient-portal access issue. It included employee personal information, payroll data, and confidential ownership information.

### Security Impact

Potential consequences include:

- Exposure of personally identifiable information.
- Employee privacy violations.
- Financial fraud and social-engineering risks.
- Disclosure of confidential ownership information.
- Reputational damage and potential regulatory consequences.

### Recommended Mitigation

- Remove database backups from publicly accessible directories.
- Store backups outside the web root in access-controlled storage.
- Encrypt backups at rest.
- Restrict backup access according to the principle of least privilege.
- Disable unnecessary directory listing.
- Review legacy resources after website migrations.
- Maintain secure backup retention and deletion procedures.
- Assess applicable data-protection and breach-notification obligations.

---

## 📊 Findings Summary and Risk Assessment

The following summary reflects the findings documented in the supplied report.

| No. | Finding | Risk Rating | Reason |
|---|---|---|---|
| 1 | Exposed web directories and application paths | High | Increased the externally discoverable attack surface |
| 2 | SQL injection enabling authentication bypass | Critical | Supported access to restricted patient-report resources |
| 3 | Weak PDF password protection | High | Password recovery was demonstrated for the three supplied PDF files |
| 4 | Sensitive information in document metadata | High | Metadata disclosed information about an internal legacy backup |
| 5 | Publicly accessible database backup | Critical | Exposed staff personal and payroll information, as well as shareholder records |

### Risk Interpretation

**Critical:** The supplied evidence demonstrated a path to highly sensitive information or a material compromise of a security boundary.

**High:** The finding materially increased exposure or supported further compromise, although its demonstrated impact was more limited than a critical finding.

Risk ratings should be reassessed after remediation and verification.

---

## 🛡️ Recommendations and Remediation

The following measures address the primary weaknesses documented in the report.

### 1. Prevent SQL Injection

- Use parameterized queries and prepared statements.
- Validate untrusted input according to application requirements.
- Avoid exposing raw database errors.
- Test authentication and input-handling logic after fixes.

### 2. Strengthen Patient-Portal Access Controls

- Enforce authentication on every protected request.
- Verify authorization for every patient record.
- Prevent access to another patient's documents.
- Implement secure session management.
- Log relevant access attempts and investigate suspicious activity.

### 3. Strengthen Document Protection

- Use strong, unique passwords when password-protected documents are necessary.
- Consider authenticated document delivery instead of distributing password-protected PDFs.
- Encrypt sensitive files at rest.
- Apply appropriate permissions and access logging.

### 4. Secure Database Backups

- Remove legacy backups from publicly accessible storage.
- Store backups outside the web root.
- Encrypt sensitive backups.
- Apply strict access controls.
- Audit backup locations regularly.

### 5. Disable Unnecessary Directory Listing

Configure the web server to prevent directory contents from being listed when no index file is present.

Review directory access rules and verify that sensitive files cannot be retrieved directly.

### 6. Remove Sensitive Document Metadata

- Strip unnecessary internal metadata before publication.
- Remove confidential comments and operational notes.
- Review document-generation and export processes.
- Test generated documents before publishing them.

### 7. Protect Employee and Financial Information

- Apply least-privilege access controls.
- Encrypt sensitive databases and backups.
- Limit access to payroll and ownership records.
- Maintain appropriate security logs.
- Establish procedures for investigating suspected data exposure.

### 8. Conduct Regular Attack-Surface Reviews

- Review exposed resources periodically.
- Include security checks in website migrations.
- Confirm that legacy resources are decommissioned.
- Reassess findings after configuration changes.
- Conduct authorized follow-up testing.

### 9. Review Data-Protection Obligations

The supplied report recommends reviewing applicable South African data-protection requirements, including POPIA, and relevant healthcare data-protection obligations.

The organization should obtain appropriate legal or compliance guidance to determine its specific obligations.

---


### 1. Reconnaissance

```markdown
![WHOIS Reconnaissance](screenshots/whois-reconnaissance.png)
```

### 2. DNS Resolution

```markdown
![DNS Resolution](screenshots/dns-resolution.png)
```

### 3. HTTP Inspection

```markdown
![HTTP Inspection](screenshots/http-inspection.png)
```

### 4. Web-Path Enumeration

```markdown
![Web-Path Enumeration](screenshots/web-path-enumeration.png)
```

### 5. Authentication Testing

```markdown
![Authentication Testing](screenshots/authentication-testing.png)
```

### 6. PDF Hash Generation

```markdown
![PDF Hash Generation](screenshots/pdf-hash-generation.png)
```

### 7. Document Metadata Analysis

```markdown
![Document Metadata Analysis](screenshots/metadata-analysis.png)
```

### 8. Findings and Risk Assessment

```markdown
![Risk Assessment](screenshots/risk-assessment.png)
```

### 9. Remediation Summary

```markdown
![Remediation Summary](screenshots/remediation-summary.png)
```

> **Note:** These are suggested image filenames. Upload your actual screenshots to the `screenshots` folder and update the filenames to match them. Do not upload unredacted patient reports, recovered passwords, national IDs, payroll records, shareholder data, or sensitive database backups.

---

## 📚 Key Learnings

This project helped develop an understanding of the following cybersecurity concepts:

- Black-box penetration-testing methodology.
- Passive and active reconnaissance.
- DNS resolution and HTTP response inspection.
- Web-directory and resource enumeration.
- SQL injection and authentication weaknesses.
- PDF password protection and offline password auditing.
- Document metadata and information disclosure.
- Database backup security.
- Personally identifiable information and confidentiality risks.
- Vulnerability classification and risk assessment.
- Security remediation and professional report writing.

The assessment also demonstrated how apparently separate weaknesses can combine to create a more serious security problem.

---

## ⚖️ Ethical and Legal Considerations

This project is documented for educational and authorized security-assessment purposes.

- Obtain written authorization before conducting penetration testing.
- Test only within the approved scope.
- Do not access or distribute unrelated sensitive information.
- Do not publish recovered credentials or confidential records.
- Store screenshots and evidence securely.
- Avoid disruptive testing unless specifically authorized.
- Report vulnerabilities responsibly to the appropriate organization.
- Verify that remediation is complete before closing findings.

**Public documentation should describe the assessment and its lessons without disclosing information that could enable unauthorized access to the assessed system.**

---

## 🏁 Conclusion

The supplied report documents a multi-stage security assessment involving reconnaissance, web-path discovery, unsafe SQL input handling, restricted patient-report access, PDF password auditing, document metadata analysis, and database backup exposure.

The findings demonstrated how weaknesses in application security, document protection, metadata handling, and backup management can combine to expose confidential information.

The principal remediation priorities are to eliminate SQL injection, strengthen authentication and authorization, improve document protection, remove sensitive backups from publicly accessible storage, and prevent internal information from being disclosed through document metadata.

This project reinforced the importance of a layered security approach, regular vulnerability assessments, secure configuration, responsible evidence handling, and effective remediation.

**Cybersecurity is not only about identifying vulnerabilities; it is also about reducing risk and protecting the confidentiality, integrity, and availability of information.**

---

## 👨‍💻 Author

**CHETAN BORADE**

- **Program:** NETWORKWALKS Cybersecurity Internship
- **Batch:** B083
- **Week:** 04
- **Project:** Black-Box Penetration Testing
- **Focus:** Web Application Security and Vulnerability Assessment

---

<p align="center">
  <b>🔐 Learn • Test • Analyze • Remediate • Secure</b>
  <br>
  <i>NETWORKWALKS | Cybersecurity Internship | Batch B083</i>
</p>
