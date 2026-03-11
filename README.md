# SOC Lab
Security Operations Center lab for hands-on practice with SIEM, log analysis, threat detection, and incident response workflows.

## 📦 Dependencies
- [Oracle VirtualBox](https://www.virtualbox.org/) — Virtualization platform;
- [Ubuntu](https://ubuntu.com/download/desktop) — Base operating system for the lab environment.
- [Docker](https://docs.docker.com/engine/install/ubuntu/) — Container platform for running SOC components.
- [Shuffler](https://github.com/Shuffle/Shuffle) — SOAR platform for security workflow automation.
- [DFIR-IRIS](https://github.com/dfir-iris/iris-web) — Incident response platform for case management and investigation tracking.

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

<details>
  <summary> Installing DFIR-IRIS</summary>
  In the DFIR-IRIS Virtual Machine:

```bash
  cd /opt
  git clone https://github.com/dfir-iris/iris-web.git
  cd iris-web
  git checkout v2.4.27
  cp .env.model .env
  docker compose up -d
```

  > ⚠️ **Warning:** For production deployments, edit the `.env` file to configure LDAP authentication, SECRET KEY, SALT, and Postgres credentials. For lab/testing purposes, the default values are sufficient.

  > 💡 **Note:** `v2.4.27` was the latest version at the time of writing. Check the [releases page](https://github.com/dfir-iris/iris-web/releases) for a newer version.

  To retrieve the default admin password:

```bash
  docker logs iriswebapp_app 2>&1 | grep 'create_safe_admin'
```

</details>