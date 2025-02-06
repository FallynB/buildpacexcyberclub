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

Using Metasploit Framework:

```bash
msfconsole
search http_version
```

This helps identify:
* Web server type (e.g., Apache)
* PHP version
* Enabled modules and extensions

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
