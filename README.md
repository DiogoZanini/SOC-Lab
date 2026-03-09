# SOC Lab
Security Operations Center lab for hands-on practice with SIEM, log analysis, threat detection, and incident response workflows.

## 📦 Dependencies
- [Oracle VirtualBox](https://www.virtualbox.org/) — Virtualization platform;
- [Ubuntu](https://ubuntu.com/download/desktop) — Base operating system for the lab environment.
- [Docker](https://docs.docker.com/engine/install/ubuntu/) — Container platform for running SOC components.
- [Shuffler](https://github.com/Shuffle/Shuffle) — SOAR platform for security workflow automation.

## 🚀 Getting Started
<details>
  <summary>Virtual Machine Configuration</summary>

  - Name: Shuffler
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

<details>
  <summary> Installing Shuffler</summary>
  In the Shuffler Virtual Machine:

```bash
  cd /opt
  git clone https://github.com/Shuffle/Shuffle
  cd Shuffle
  docker compose up -d
```

> 💡 **Note:** Tested with the current version of Shuffle. Older versions may require manual permission adjustments on the `shuffle-database` directory.

</details>