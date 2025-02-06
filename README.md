# Understanding HTTP Security: A Practical Guide

## Introduction to Port 80 Vulnerabilities

This guide demonstrates how to identify and understand vulnerabilities in HTTP services running on Port 80. This knowledge is essential for system administrators and security professionals to better protect their systems.

## Why Focus on Port 80?

HTTP (Hypertext Transfer Protocol) running on Port 80 is a fundamental protocol for web services. We focus on it because:

* It's commonly used for web traffic
* It transmits data in plaintext, making it easier to analyze
* Many legacy systems still use HTTP instead of HTTPS
* It's often a starting point for security assessments

## Required Tools

1. Metasploitable - A purposely vulnerable virtual machine for security testing
2. Kali Linux - Security-focused Linux distribution containing:
   * Nmap - Network scanning and reconnaissance tool
   * Various security assessment utilities
3. Web browser - For verifying findings

## Technical Breakdown

### Step 1: Initial Reconnaissance with Nmap

Command used: `nmap -sV [IP] -p80`

![Initial Nmap Scan Results](base_nmap_scan.png)

Let's break down this command:
* `-sV`: Performs version detection of services
* `-p80`: Specifically targets port 80
* This scan identifies:
   * Running web server software
   * Version information
   * Operating system details

### Step 2: Service Enumeration
1. Launch Metasploit Framework
`msfconsole`

2. Search for HTTP information gathering module
`search http_version`

3. Select the HTTP version scanner
`use auxiliary/scanner/http/http_version`

4. View available options
`show options`

5. Set your target IP
`set RHOSTS [TARGET_IP]`

6. Execute the scan
`run`
** Note: Run the scan to gather detailed information about what services and applications are running on this port. This reconnaissance step will help identify the specific technologies and versions being used by the target web server. Once we have this information, we can better understand what potential vulnerabilities or misconfigurations might exist and determine our next steps for enumeration.**



### Step 3: Directory Structure Analysis

Using built-in scanners:

```bash
search dir_scanner
use [scanner_number]
set RHOSTS [target_IP]
run
```

Key findings:
* Web root directory structure
* Configuration files location
* Administrative interfaces
* Backup files
* Hidden directories
