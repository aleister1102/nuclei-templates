# Nuclei Templates - Directory Structure and Functions

## Overview
This repository contains Nuclei templates used to scan and detect security vulnerabilities, misconfigurations, and other security issues. Below is a detailed description of the functionality of each directory.

## 📁 Main Directory Structure

### ☁️ **cloud/**
Contains templates for scanning cloud computing services and configurations.

- **alibaba/** - Templates for scanning Alibaba Cloud services
- **aws/** - Templates for scanning Amazon Web Services (AWS)
- **azure/** - Templates for scanning Microsoft Azure services
- **enum/** - Templates for enumerating cloud service information
- **gcp/** - Templates for scanning Google Cloud Platform (GCP) services
- **kubernetes/** - Templates for scanning Kubernetes clusters and container orchestration

### 💻 **code/**
Contains templates for analyzing and auditing source code.

- **audit/** - Templates for source code security auditing
- **cves/** - Templates for detecting CVEs in source code
- **privilege-escalation/** - Templates for detecting privilege escalation vulnerabilities
- **windows/** - Templates specialized for Windows systems

### 🛡️ **dast/**
Dynamic Application Security Testing - Testing dynamic web application security.

- **cves/** - Templates for detecting CVEs through DAST
- **vulnerabilities/** - Templates for detecting web application vulnerabilities

### 🌐 **dns/**
Contains templates for checking DNS configuration and security.

- **azure-takeover-detection.yaml** - Detects Azure DNS takeover possibilities
- **bimi-detect.yaml** - Detects BIMI (Brand Indicators for Message Identification) configuration
- **caa-fingerprint.yaml** - Fingerprints CAA (Certificate Authority Authorization) records
- **detect-dangling-cname.yaml** - Detects dangling CNAME records
- **dmarc-detect.yaml** - Detects DMARC configuration
- **dns-rebinding.yaml** - Detects DNS rebinding vulnerabilities
- **dns-saas-service-detection.yaml** - Detects SaaS services via DNS
- **dns-waf-detect.yaml** - Detects WAF via DNS
- **dnssec-detection.yaml** - Checks DNSSEC configuration
- **ec2-detection.yaml** - Detects EC2 instances via DNS
- **elasticbeanstalk-takeover.yaml** - Detects Elastic Beanstalk takeover possibilities
- **mx-fingerprint.yaml** - Fingerprints MX records
- **mx-service-detector.yaml** - Detects email services via MX records
- **nameserver-fingerprint.yaml** - Fingerprints nameservers
- **ptr-fingerprint.yaml** - Fingerprints PTR records
- **servfail-refused-hosts.yaml** - Detects hosts refusing DNS queries
- **soa-detect.yaml** - Detects SOA records
- **spf-record-detect.yaml** - Detects SPF records
- **spoofable-spf-records-ptr.yaml** - Detects spoofable SPF records
- **txt-fingerprint.yaml** - Fingerprints TXT records
- **txt-service-detect.yaml** - Detects services via TXT records
- **worksites-detection.yaml** - Detects work websites

### 📄 **file/**
Contains templates for file analysis and malware detection.

- **android/** - Templates for analyzing Android files (APK)
- **audit/** - Templates for file security auditing
- **bash/** - Templates for analyzing Bash scripts
- **electron/** - Templates for analyzing Electron applications
- **js/** - Templates for analyzing JavaScript files
- **keys/** - Templates for detecting secret keys and API keys
- **logs/** - Templates for analyzing log files
- **malware/** - Templates for malware detection
- **nodejs/** - Templates for analyzing Node.js applications
- **perl/** - Templates for analyzing Perl scripts
- **php/** - Templates for analyzing PHP files
- **python/** - Templates for analyzing Python scripts
- **url-analyse/** - Templates for analyzing URLs in files
- **webshell/** - Templates for detecting webshells
- **xss/** - Templates for detecting XSS in files

### 🖥️ **headless/**
Contains templates using headless browsers for testing.

- **cookie-consent-detection.yaml** - Detects cookie consent banners
- **dvwa-headless-automatic-login.yaml** - Automatic DVWA login
- **extract-urls.yaml** - Extracts URLs from websites
- **headless-open-redirect.yaml** - Detects open redirects
- **postmessage-outgoing-tracker.yaml** - Tracks outgoing postMessages
- **postmessage-tracker.yaml** - Tracks postMessages
- **prototype-pollution-check.yaml** - Checks for prototype pollution
- **screenshot.yaml** - Takes website screenshots
- **webpack-sourcemap.yaml** - Detects webpack sourcemaps
- **window-name-domxss.yaml** - Detects DOM XSS via window.name
- **cves/** - CVEs detected using headless browsers
- **technologies/** - Technology detection via headless browsers
- **vulnerabilities/** - Vulnerabilities detected via headless browsers

### 🛠️ **helpers/**
Contains supporting files and payloads.

- **payloads/** - Payloads for testing
- **wordlists/** - Word lists for brute forcing
- **wordpress/** - Helpers for WordPress

### 🌍 **http/**
The largest directory containing HTTP templates for scanning web applications.

- **cnvd/** - Templates for China National Vulnerability Database
- **credential-stuffing/** - Templates for credential stuffing attacks
- **cves/** - Templates for detecting CVEs via HTTP
- **default-logins/** - Templates for checking default logins
- **exposed-panels/** - Templates for detecting exposed admin panels
- **exposures/** - Templates for detecting information exposures
- **fuzzing/** - Templates for HTTP fuzzing
- **global-matchers/** - Global matchers for HTTP
- **honeypot/** - Templates for detecting honeypots
- **iot/** - Templates for IoT devices
- **miscellaneous/** - Other HTTP templates
- **misconfiguration/** - Templates for detecting HTTP misconfigurations
- **osint/** - Templates for open source intelligence gathering
- **takeovers/** - Templates for detecting subdomain takeovers
- **technologies/** - Templates for detecting web technologies
- **token-spray/** - Templates for token spray attacks
- **vulnerabilities/** - Templates for detecting web vulnerabilities

### ⚡ **javascript/**
Templates for testing JavaScript and Node.js.

- **backdoor/** - Detects backdoors in JavaScript
- **cves/** - CVEs in JavaScript
- **default-logins/** - Default logins in JS apps
- **detection/** - JavaScript framework/library detection
- **enumeration/** - JavaScript information enumeration
- **misconfiguration/** - JavaScript misconfigurations
- **udp/** - JavaScript templates for UDP

### 🔌 **network/**
Templates for testing network services and protocols.

- **backdoor/** - Detects network backdoors
- **c2/** - Detects Command & Control servers
- **cves/** - CVEs in network services
- **default-login/** - Default logins for network services
- **detection/** - Network service detection
- **enumeration/** - Network information enumeration
- **exposures/** - Detects exposed network information
- **honeypot/** - Detects network honeypots
- **jarm/** - JARM fingerprinting
- **misconfig/** - Network misconfigurations
- **vulnerabilities/** - Network vulnerabilities

### 📊 **passive/**
Templates for passive scanning without sending harmful payloads.

- **cves/** - CVEs detected passively

### 👤 **profiles/**
Contains configuration profiles for different types of scans.

### 🔒 **ssl/**
Templates for checking SSL/TLS configuration.

### 🔄 **workflows/**
Contains workflows combining multiple templates.

- **apisix-workflow.yaml** - Workflow for checking Apache APISIX

## 📚 Supporting Files

- **cves.json** - List of supported CVEs
- **contributors.json** - List of contributors
- **templates-checksum.txt** - Template checksums
- **TEMPLATES-STATS.json** - Template statistics
- **wappalyzer-mapping.yml** - Mapping with Wappalyzer

## 🎯 Usage

Each directory contains YAML templates that can be used with the Nuclei scanner:

```bash
# Scan with specific template
nuclei -t http/cves/ -u target.com

# Scan with workflow
nuclei -w workflows/apisix-workflow.yaml -u target.com

# Scan with multiple templates
nuclei -t http/exposures/,network/cves/ -u target.com
```

## ⚠️ Important Notes

- Only use these templates on systems you own or have permission to test
- Some templates may cause high load on target systems
- Always comply with laws and regulations regarding information security

## 🤝 Contributing

To contribute new templates, please refer to the `CONTRIBUTING.md` file and guidelines in the `.github/` directory.