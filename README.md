# SOC Lab
Security Operations Center lab for hands-on practice with SIEM, log analysis, threat detection, and incident response workflows.

[**PT-BR**](./docs/README.pt-br.md)

## 📦 Dependencies
- [Oracle VirtualBox](https://www.virtualbox.org/) — Virtualization platform;
- [Ubuntu](https://ubuntu.com/download/desktop) — Base operating system for the lab environment.
- [Docker](https://docs.docker.com/engine/install/ubuntu/) — Container platform for running SOC components.
- [Shuffler](https://github.com/Shuffle/Shuffle) — SOAR platform for security workflow automation.
- [DFIR-IRIS](https://github.com/dfir-iris/iris-web) — Incident response platform for case management and investigation tracking.
- [Ollama](https://github.com/ollama/ollama) — Local AI model runner for alert enrichment and automated threat analysis.

## Infrastructure

### VM 1 — Shuffler
- **OS:** Ubuntu Desktop (GUI)
- **Components:** Shuffler
- **RAM:** 8192 MB (8 GB)
- **CPUs:** 4
- **Disk:** 80 GB
- **Network:** NAT

### VM 2 — DFIR-IRIS
- **OS:** Ubuntu Live Server (CLI)
- **Components:** DFIR-IRIS
- **RAM:** 4096 MB (4 GB)
- **CPUs:** 2
- **Disk:** 25 GB
- **Network:** NAT

## 🚀 Getting Started
<details>
  <summary> Installing Docker in both machines</summary>
  In both the Shuffler and DFIR-IRIS Virtual Machines:

```bash
curl https://get.docker.com | bash
```

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

## Troubleshooting
Common issues and their solutions.

### Connection reset during image pull (read: connection reset by peer)
- **Problem:** `read tcp [abcd:abcd:abcd]:60900->[abcd:abcd:abcd]:443: read: connection reset by peer` — Docker using IPv6 caused unstable downloads.
- **Solution:**
```bash
  sysctl -w net.ipv6.conf.all.disable_ipv6=1
```
