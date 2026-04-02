# Module 14: Software Security Engineering

## Learning Objectives
- Integrate security across the SDLC (Secure SDLC).
- Apply threat modeling (STRIDE, DREAD).
- Implement secure design principles (least privilege, defense in depth).
- Test for common vulnerabilities (OWASP Top 10).

## Key Topics

### 1. Security Engineering Fundamentals
- **CIA Triad**: Confidentiality, Integrity, Availability.
- **Additional**: Authentication, Authorization, Non-repudiation.
- **Security vs. Safety**:
  - Security: Malicious intent.
  - Safety: Accidental harm.

### 2. Secure Software Development Lifecycle (SSDLC)
- **Requirements**: Abuse cases, security stories.
- **Design**: Threat modeling, attack surface analysis.
- **Implementation**: Secure coding standards, static analysis.
- **Testing**: SAST, DAST, penetration testing.
- **Maintenance**: Patch management, vulnerability disclosure.

### 3. Threat Modeling
- **STRIDE** (Microsoft):
  - Spoofing, Tampering, Repudiation, Information disclosure, Denial of service, Elevation of privilege.
- **DREAD** (Risk rating):
  - Damage, Reproducibility, Exploitability, Affected users, Discoverability.
- **Tools**: Microsoft Threat Modeling Tool, OWASP Threat Dragon.

### 4. Secure Design Principles (Saltzer & Schroeder)
- Least privilege
- Defense in depth
- Fail-safe defaults
- Economy of mechanism
- Complete mediation
- Open design
- Separation of privilege
- Least common mechanism
- Psychological acceptability

### 5. Common Vulnerabilities & OWASP Top 10
- **OWASP Top 10 (2021)** highlights:
  - A01: Broken Access Control
  - A02: Cryptographic Failures
  - A03: Injection (SQL, NoSQL, OS)
  - A04: Insecure Design
  - A05: Security Misconfiguration
  - A06: Vulnerable Components
  - A07: Identification/Auth Failures
  - A08: Software/Data Integrity Failures
  - A09: Logging & Monitoring Failures
  - A10: SSRF

### 6. Security Testing
- **Static (SAST)** : Find flaws in source code (SonarQube, Checkmarx).
- **Dynamic (DAST)** : Test running app (OWASP ZAP, Burp Suite).
- **Penetration Testing** (manual ethical hacking).
- **Fuzzing** (random/invalid inputs).

### 7. Security Standards & Regulations
- **ISO/IEC 27034** (Application security).
- **NIST SSDF** (Secure Software Development Framework).
- **GDPR**, **HIPAA**, **PCI DSS** (domain-specific).

## Learning Activities
- Threat model a simple web login system using STRIDE.
- Use OWASP ZAP to find vulnerabilities in a deliberately vulnerable app (e.g., WebGoat, DVWA).

## Assessment
- Secure design document: threat model + countermeasures for a given system.
- Vulnerability report (findings, severity, fixes) from a testing exercise.

## References
- Howard, M., Lipner, S. *The Security Development Lifecycle*.
- OWASP Foundation resources (owasp.org).
- Anderson, R. *Security Engineering*.
