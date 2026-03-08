# SOC Lab
Security Operations Center lab for hands-on practice with SIEM, log analysis, threat detection, and incident response workflows.

## 📦 Dependencies
- [Oracle VirtualBox](https://www.virtualbox.org/) — Virtualization platform;
- [Ubuntu](https://ubuntu.com/download/desktop) — Base operating system for the lab environment.
- [Docker](https://docs.docker.com/engine/install/ubuntu/) — Container platform for running SOC components.

## 🚀 Getting Started
<details>
  <summary>Virtual Machine Configuration</summary>

  - Base Memory: 8192 MB (8 GB);
  - Number of CPUs: 4 CPUs;
  - Disk Size: 25 GB;
  - Network Adapter: NAT (for internet access during setup).

  > 💡 **Note:** These specifications can be adjusted based on your host machine resources and lab requirements.

</details>

<details>
  <summary> Installing Docker</summary>
```bash
  curl https://get.docker.com | bash
```

</details>

<details>
  <summary> Cloning the VM for DFIR-IRIS</summary>

  In VirtualBox, right-click the main VM → **Clone**:
  - Name: `DFIR-IRIS`
  - Clone type: **Full clone**

  > 💡 **Note:** Cloning avoids reinstalling the OS and Docker from scratch.

</details>