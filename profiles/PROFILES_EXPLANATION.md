# Explanation of Files in the Profiles Directory

The `profiles/` directory contains YAML configuration files designed to run Nuclei with specific scanning objectives. Each profile is optimized for different security scenarios.

## 📋 List and Explanation of Profiles

### 🎯 **recommended.yml** 
**Main profile recommended for general scanning**
- **Purpose**: Provides balanced and efficient scanning experience for most scenarios
- **Includes**: All severity levels (critical, high, medium, low, unknown)
- **Template types**: DNS, SSL, TCP, HTTP, JavaScript
- **Excludes**: Some specific CVEs to avoid false positives
- **Usage**: `nuclei -profile recommended -u https://example.com`

### 🌩️ **cloud.yml**
**Profile for Cloud environments**
- **Purpose**: Detect vulnerabilities and misconfigurations in cloud environments
- **Tags**: cloud, devops
- **Application**: Cloud infrastructure security testing
- **Usage**: `nuclei -profile cloud -u https://example.com`

### 🛡️ **cves.yml**
**Profile focused on CVE (Common Vulnerabilities and Exposures)**
- **Purpose**: Detect vulnerabilities published in the CVE database
- **Templates**: http/cves/, http/cnvd/, network/cves/, javascript/cves/
- **Importance**: Essential for patching and risk mitigation
- **Usage**: `nuclei -profile cves -u https://example.com`

### 🔍 **osint.yml** 
**Profile for Open Source Intelligence**
- **Purpose**: Gather intelligence information from open sources
- **Tags**: osint, honeypot, backdoor, c2, exposures, malware, enum, phishing
- **Application**: Threat hunting, reconnaissance
- **Usage**: `nuclei -profile osint -u https://example.com`

### ⬆️ **privilege-escalation.yml**
**Profile for Local Privilege Escalation**
- **Purpose**: Detect local privilege escalation vulnerabilities
- **Features**: Enable code templates (`code: true`)
- **Tags**: privesc, local
- **Application**: Post-exploitation testing
- **Usage**: `nuclei -profile privilege-escalation`

### 📊 **compliance.yml**
**Profile for Compliance and Standards**
- **Purpose**: Ensure compliance with security standards
- **Tags**: misconfig, cve, exposure, default-login, xss, lfi, edb, rce, sqli
- **Application**: Compliance audit, regulatory requirements
- **Usage**: `nuclei -profile compliance -u https://example.com`

### 🔑 **default-login.yml**
**Profile for Default Credentials checking**
- **Purpose**: Detect systems using default login credentials
- **Templates**: http/default-logins/, network/default-login/, javascript/default-logins/
- **Risk**: High - commonly targeted by attackers
- **Usage**: `nuclei -profile default-login -u https://example.com`

### 🏴‍☠️ **subdomain-takeovers.yml**
**Profile for Subdomain Takeover**
- **Purpose**: Detect subdomain takeover possibilities
- **Templates**: http/takeovers/, dns/azure-takeover-detection.yaml
- **Scenario**: DNS pointing to deprovisioned cloud resources
- **Usage**: `nuclei -profile subdomain-takeovers -u https://www.example.com`

### ⚙️ **misconfigurations.yml**
**Profile for Misconfiguration detection**
- **Purpose**: Detect security misconfigurations
- **Focus**: Infrastructure and application misconfigurations
- **Common issues**: Open ports, exposed services, weak configurations

### 📝 **pentest.yml**
**Profile for Penetration Testing**
- **Purpose**: Comprehensive testing for penetration testing engagements
- **Scope**: Wide range of vulnerabilities
- **Usage**: Professional security assessments

### 🔐 **kev.yml**
**Profile for Known Exploited Vulnerabilities**
- **Purpose**: Focus on CVEs with public exploits
- **Priority**: High-risk vulnerabilities
- **Source**: CISA KEV Catalog

### 🪟 **windows-audit.yml**
**Profile for Windows Security Audit**
- **Purpose**: Specialized for Windows environments
- **Focus**: Windows-specific vulnerabilities and configurations
- **Usage**: Windows infrastructure assessment

### 🌐 **wordpress.yml**
**Profile for WordPress Security**
- **Purpose**: Specialized for WordPress sites
- **Coverage**: WordPress plugins, themes, core vulnerabilities
- **Common**: Very popular CMS target

## ☁️ **Cloud-Specific Profiles**

### **aws-cloud-config.yml**
- **Purpose**: AWS Access Control Lists (ACLs) scanning
- **Features**: Enable code templates, region variable (us-east-1)
- **Tags**: aws-cloud-config

### **azure-cloud-config.yml**
- **Purpose**: Microsoft Azure security assessment
- **Focus**: Azure-specific services and configurations

### **gcp-cloud-config.yml**
- **Purpose**: Google Cloud Platform security scanning
- **Focus**: GCP services and IAM configurations

### **alibaba-cloud-config.yml**
- **Purpose**: Alibaba Cloud security assessment
- **Region**: China-focused cloud provider

### **k8s-cluster-security.yml**
- **Purpose**: Kubernetes cluster security assessment
- **Focus**: Container orchestration vulnerabilities
- **Coverage**: Kubernetes misconfigurations, RBAC issues

### 📋 **all.yml**
**Profile running all templates**
- **Purpose**: Comprehensive scan with all available templates
- **Warning**: Very resource intensive, may produce many results
- **Usage**: Full security assessment

## 🎯 **How to use Profiles**

### Basic syntax:
```bash
nuclei -profile <profile-name> -u <target>
```

### Examples:
```bash
# Recommended scan
nuclei -profile recommended -u https://example.com

# CVE scan
nuclei -profile cves -u https://example.com

# Cloud scan
nuclei -profile cloud -u https://cloudapp.com

# WordPress scan
nuclei -profile wordpress -u https://myblog.com

# Scan with multiple targets
nuclei -profile compliance -l targets.txt
```

## 📝 **Profile YAML Structure**

Each profile can contain:

- **`tags:`** - Filter templates by tags
- **`templates:`** - Specify specific template directories
- **`severity:`** - Filter by severity level
- **`type:`** - Template type (http, dns, ssl, tcp, javascript)
- **`exclude-id:`** - Exclude specific template IDs
- **`include-tags:`** - Include additional tags
- **`code:`** - Enable/disable code templates
- **`var:`** - Variables for templates

## ⚠️ **Important Notes**

1. **Performance**: Some profiles like `all.yml` are very resource-intensive
2. **False Positives**: The `recommended.yml` profile has been tuned to reduce false positives
3. **Compliance**: Compliance profiles need to be customized according to specific requirements
4. **Cloud**: Cloud profiles require appropriate credentials and permissions
5. **Legal**: Always ensure you have permission to test on target systems

## 🛠️ **Custom Profiles**

You can create custom profiles by:

1. Copy an existing profile
2. Modify tags, templates, severity according to needs
3. Test with small target first
4. Document purpose and usage of the profile

Example custom profile:
```yaml
# my-custom-profile.yml
severity:
  - critical
  - high
tags:
  - rce
  - sqli
  - xss
exclude-id:
  - CVE-2021-12345
```
