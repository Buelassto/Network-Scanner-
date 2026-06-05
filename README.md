Here is the fully refined, professional version of your README.md. It has been restructured with high-level technical terminology, precise technical descriptions, and clean formatting suitable for enterprise-grade open-source repositories or professional portfolios.Markdown# Network Asset Discovery Utility

An enterprise-ready, high-speed Python implementation designed for rapid network reconnaissance and asset discovery. Leveraging native network mapping engine sweeps, this utility programmatically enumerates active endpoints within a specified network block and aggregates the results into an optimized single-line telemetry output—ideal for decoupling discovery and passing targets cleanly into downstream vulnerability management pipelines.

[![Python Version](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![Nmap Dependency](https://img.shields.io/badge/Dependency-Nmap-orange.svg)](https://nmap.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)

---

## ⚡ Architectural Features

* **Low-Overhead Infrastructure Sweeps:** Implements optimized ICMP echo request ping sweeps (`-sn`) to establish live asset counts without executing intrusive port-level mapping.
* **Subprocess Isolation:** Avoids high-overhead abstractions by executing native system binaries directly via strict execution streams, ensuring bare-metal performance.
* **Deterministic Boundary Protection:** Enforces rigorous execution constraints via configurable process loop timeouts, preventing runaway processes on high-latency nodes.
* **Structured Stream Outputs:** Normalizes asynchronous network outputs into an isolated, standard-out text signature (`FOUND_HOSTS: ip1, ip2...`) engineered for direct parsing by automation tooling, SIEM inputs, or shell pipes.
* **Granular Congestion Control:** Native support for engine timing presets (`-T0` through `-T5`) to explicitly balance operational stealth against network throughput capacity.

---

## 📋 Environment Configuration

### 1. System Binaries
The host environment must contain a valid installation of the `nmap` core binary.

* **macOS** (via Homebrew):
  ```bash
  brew install nmap
Linux (Debian/Ubuntu):Bashsudo apt update && sudo apt install nmap -y
2. Runtime RequirementsThis utility utilizes native Python standard library streams (subprocess, re, sys, argparse). No third-party virtual environments or external pip wrappers are required for distribution.🚀 Deployment GuideBasic Inventory PassExecute an asset discovery scan across a standard Class C target allocation:Bashpython3 discover.py
Advanced Parameterized ScanExecute an aggressive target validation pass targeting an internal data-center allocation with a fixed 60-second execution lifecycle:Bashpython3 discover.py --cidr 10.0.0.0/24 --timeout 60 --timing 5
Configuration SpecificationCLI ParameterTypeDefault ValueTechnical Specification--cidrString192.168.1.0/24Target network architecture block using standard CIDR notation.--timeoutInteger120Maximum operational execution loop window threshold in seconds.--timingString4Engine execution profiles scaling from 0 (Paranoid) up to 5 (Insane).📊 Telemetry Output PreviewUpon a successful network segment pass, the utility structures and isolates live hosts cleanly to standard output:PlaintextFOUND_HOSTS: 192.168.1.1, 192.168.1.15, 192.168.1.34, 192.168.1.100
🛑 Regulatory Compliance & Legal DisclaimerThis infrastructure auditing software is designed exclusively for authorized network inventory validation, enterprise asset management, and authorized perimeter discovery. Deploying passive or active reconnaissance against third-party environments without an explicitly executed Rules of Engagement documentation and written clearance from system stakeholders constitutes an unauthorized network intrusion. The developer assumes no civil or criminal liability for malicious modifications, deployment errors, or compliance violations stemming from this utility.
