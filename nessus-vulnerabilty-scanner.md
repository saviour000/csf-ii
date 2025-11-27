
````markdown
# Vulnerability Assessment & Malware Analysis Lab

## Part 1: Nessus Vulnerability Scanner

### Objectives
- Install and configure Nessus  
- Run basic, credentialed, and policy-based scans  
- Perform vulnerability analysis, prioritization, and remediation  
- Export and present scan reports  

---

## Lab Environment Setup

### Analyst VM
- Linux or Windows  
- Nessus installed  

### Target VMs
- Windows Server  
- Ubuntu Server  
- Metasploitable 2/3  
- DVWA  

### Network
- Isolated NAT or Host-only network  

---

## Step 1 — Nessus Installation

### Linux Installation Example

```bash
sudo dpkg -i Nessus-<version>-debian6_amd64.deb
sudo systemctl start nessusd
````

### Web Setup

Open browser:

```
https://localhost:8834
```

Steps:

1. Create admin account
2. Activate using license key

---

## Step 2 — Basic Network Scan

### Steps

1. Go to **Scans → New Scan**
2. Choose **Basic Network Scan**
3. Configure:

   * **Name:** `Lab Scan 1`
   * **Targets:** IP range of your lab VMs
4. Save and launch

### Deliverables

* Host discovery results
* List of open ports

---

## Step 3 — Credentialed Scan

### Steps

1. Create new scan → **Advanced Scan**
2. Add credentials:

   * SSH for Linux
   * SMB/WinRM for Windows
3. Run scan

### Deliverables

* Findings like:

  * Missing patches
  * Weak passwords
  * Misconfigurations

---

## Step 4 — Policy Creation

### Steps

1. Clone **Basic Network Scan** policy
2. Modify plugin families

   * Enable web application checks
3. Save and run the policy

### Deliverables

* Policy configuration file
* Scan report

---

## Step 5 — Report Analysis

### Steps

1. Open scan results
2. Identify **Top 5 Critical Vulnerabilities**
3. Map them to CVEs
4. Export:

   * PDF report
   * CSV report

### Deliverables

* Executive summary
* Technical annex

---

## Step 6 — Vulnerability Remediation

### Steps

1. Select:

   * One Windows host
   * One Linux host
2. Apply security fixes:

   * Install patches
   * Disable weak services
3. Re-scan to validate remediation

### Deliverables

* Before/after comparison report

---

# Part 2: ANY.RUN Malware Sandbox

## Objectives

* Submit files and URLs
* Perform dynamic malware analysis
* Extract Indicators of Compromise (IOCs)
* Create detection rules

---

## Step 1 — Access ANY.RUN

1. Go to: [https://app.any.run](https://app.any.run)
2. Sign in to your account
3. Explore dashboard

---

## Step 2 — Sample Upload

### Steps

1. Click **New Task**
2. Choose environment: **Windows 10**
3. Upload file or submit URL
4. Adjust network settings
5. Start analysis

### Deliverable

* Initial analysis report link

---

## Step 3 — Interactive Monitoring

### Observe

* Process tree
* DNS requests
* HTTP traffic
* Dropped files
* Registry changes

### Deliverable

* Annotated screenshots of process tree

---

## Step 4 — IOC Extraction

### Extract

* Domains
* IP addresses
* File hashes

### Export

* PCAP file
* IOC list

### Sample Suricata Rule

```text
alert http $HOME_NET any -> $EXTERNAL_NET any \
(msg:"Malware C2 domain"; http_host; content:"malicious-site.com"; sid:1000002; rev:1;)
```

### Deliverables

* IOC list
* Suricata / YARA detection rules

---

## Step 5 — Reporting

### Include

* Screenshots
* Process details
* Registry changes
* File operations

### Deliverable

* Final malware analysis report (PDF/HTML)

---

## Step 6 — PCAP Analysis with Wireshark

### Steps

1. Download PCAP from ANY.RUN
2. Open in Wireshark
3. Analyze suspicious C2 traffic

### Deliverable

* Screenshots of malicious packets

---

## Step 7 — Combined Workflow

### Process

1. Use Nessus scan to identify suspicious files
2. Upload suspicious file to ANY.RUN
3. Correlate:

   * Nessus findings
   * Malware IOCs

### Deliverable

* Correlation & analysis report


If you want it broken into separate `.md` files (Nessus + ANY.RUN), just tell me.
```
