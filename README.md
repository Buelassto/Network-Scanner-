Markdown# Network Vulnerability Scan Framework

A modular, automated Python utility for host discovery, port enumeration, and network vulnerability assessment using Nmap. This tool orchestrates low-level security scans and compiles complex raw data into formatted, actionable **Markdown reports**.

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![Nmap](https://img.shields.io/badge/Dependency-Nmap-orange.svg)](https://nmap.org/)

---

## 🛠️ Key Capabilities

* **Automated Asset Discovery:** Executes a rapid ICMP ping sweep to map live hosts before scanning, preventing wasted network overhead.
* **Service & Port Mapping:** Runs multi-threaded TCP SYN stealth scans (`-sS`) against target nodes to discover open doors securely.
* **NSE Vulnerability Integration:** Automatically invokes selected Nmap Scripting Engine (NSE) scripts (defaults to `vuln` and `default`).
* **Heuristic Risk Tagging:** Dynamically parses raw output lines to flag findings by threat levels: `Critical`, `High`, `Medium`, `Low`, or `Info`.
* **Archived MD Reporting:** Generates a structured Markdown table summarizing targets, services, and risk vectors for simple tracking over time.
* **Simulation Mode:** Includes a comprehensive `--dry-run` flag to safely log scheduled Nmap execution chains without sending target packets.

---

## 📋 Prerequisites

Ensure your host environment has the system binaries and library dependencies installed before execution.

### 1. Core Binaries
* **macOS** (Homebrew):
  ```bash
  brew install nmap
Linux (Debian/Ubuntu):Bashsudo apt update && sudo apt install nmap -y
2. Python EnvironmentInstall script package requirements via pip:Bashpip install rich python-nmap
🚀 Usage Guide⚠️ Privilege Elevation Required: Because this utility triggers low-level TCP SYN Stealth Scans (-sS), the script must be run with administrative privileges (sudo).Basic CommandBashsudo python3 scan.py --network 192.168.1.0/24
Advanced ScanCustomizing ports, targeted scripts, and designated output paths:Bashsudo python3 scan.py --network 10.0.0.0/24 --ports 22,80,443,8080 --scripts vuln --output custom_audit.md
Configuration OptionsArgumentTypeDefault ValueDescription--networkStringRequiredTarget network range in standard CIDR notation.--portsString1-1000Port range configuration for the SYN discovery step.--scriptsStringvuln,defaultTargeted Nmap NSE script categories to process.--outputStringscan_report.mdTarget file destination path for the final Markdown output.--dry-runFlagFalseSimulates and logs execution commands without scanning.📊 Output PreviewBelow is an example of how your final report looks when written to your repository directory:Markdown# Network Vulnerability Report

Network: 192.168.1.0/24
Generated: 2026-06-05 06:00 UTC

## Host: 192.168.1.50

| Port | Service | Severity | Details |
|------|---------|----------|---------|
| 80   | http    | High     | vulnerable-http-exploit: <br> CVE-202X-XXXX <br> High risk exposure. |
| 443  | https   | Info     | ssl-cert: <br> Valid until 2028. |
🛑 Legal & Ethical DisclaimerThis application is designed strictly for educational purposes, authorized infrastructure hardening, and defensive security auditing. Scanning target networks without prior, explicit written authorization from the system owners is strictly prohibited and violates local and international cybersecurity regulations. The developer accepts no legal liability or responsibility for unauthorized deployment or systemic damages caused by this tool.
