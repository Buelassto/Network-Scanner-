# Fast Network Host Discovery Tool

A lightweight, high-speed Python utility designed for rapid asset discovery across a network block. By utilizing native Nmap ping sweeps, it efficiently identifies live hosts and outputs a single, clean string optimized for pipe-lining into downstream security or automation workflows.

[![Python](https://img.shields.io/badge/Python-3.x-blue.svg)](https://www.python.org/)
[![Nmap](https://img.shields.io/badge/Dependency-Nmap-orange.svg)](https://nmap.org/)

---

## ⚡ Key Features

* **Subprocess Execution Architecture:** Directly invokes system native utilities without dependency bloat.
* **Streamlined Output Formatting:** Isolates active endpoints into a unified string (`FOUND_HOSTS: ip1, ip2...`) perfect for automated parsing by security frameworks.
* **Performance Control:** Customizable execution thresholds and aggressive Nmap timing presets (`-T0` to `-T5`) to scale across massive ranges.
* **Robust Exception Handling:** Gracefully catches hardware latency, terminal timeouts, and environment configuration conflicts.

---

## 📋 Prerequisites

### 1. Install Nmap Binary
* **macOS** (Homebrew):
```bash
  brew install nmap
Linux (Debian/Ubuntu):Bash  sudo apt update && sudo apt install nmap -y
🚀 Usage GuideBasic ExecutionScan the default network range (192.168.1.0/24):Bashpython3 discover.py
Advanced Custom Target ScanTarget a specific block with a custom 60-second execution window and customized aggressive scanning speed:Bashpython3 discover.py --cidr 10.0.0.0/24 --timeout 60 --timing 5
Configuration OptionsArgumentTypeDefault ValueDescription--cidrString192.168.1.0/24The targeted network range using CIDR block notation.--timeoutInteger120Max duration allowed for the Nmap process loop in seconds.--timingString4Nmap timing template speeds ranging from 0 (Paranoid) to 5 (Insane).📊 Terminal Output PreviewPlaintextFOUND_HOSTS: 192.168.1.1, 192.168.1.15, 192.168.1.34, 192.168.1.100
🛑 Legal DisclaimerThis utility is structured specifically for authorized infrastructure assessment, network visibility tracking, and defensive inventory auditing. Conducting target reconnaissance on external platforms without express written documentation from network administrators violates structural security regulations. The author assumes no accountability for unauthorized software deployment.
