# SOC Lab
Laboratório de Centro de Operações de Segurança para prática hands-on com SIEM, análise de logs, detecção de ameaças e fluxos de resposta a incidentes.

[**EN-US**](../README.md)

## 📦 Dependências
- [Oracle VirtualBox](https://www.virtualbox.org/) — Plataforma de virtualização;
- [Ubuntu Desktop](https://ubuntu.com/download/desktop) — Sistema operacional base para o ambiente do laboratório.
- [Docker](https://docs.docker.com/engine/install/ubuntu/) — Plataforma de contêineres para executar componentes do SOC.
- [Shuffler](https://github.com/Shuffle/Shuffle) — Plataforma SOAR para automação de fluxos de segurança.
- [DFIR-IRIS](https://github.com/dfir-iris/iris-web) — Plataforma de resposta a incidentes para gerenciamento de casos e rastreamento de investigações.

## Infraestrutura

### VM 1 — Shuffler
- **SO:** Ubuntu Desktop (GUI)
- **Componentes:** Shuffler
- **RAM:** 8192 MB (8 GB)
- **CPUs:** 4
- **Disco:** 25 GB
- **Rede:** NAT

### VM 2 — DFIR-IRIS
- **SO:** Ubuntu Live Server (CLI)
- **Componentes:** DFIR-IRIS
- **RAM:** 4096 MB (4 GB)
- **CPUs:** 2
- **Disco:** 25 GB
- **Rede:** NAT

## 🚀 Primeiros Passos
<details>
  <summary> Instalando o Docker em ambas as máquinas</summary>
  Em ambas as Máquinas Virtuais Shuffler e DFIR-IRIS:

```bash
  curl https://get.docker.com | bash
```

</details>

<details>
  <summary>Instalando o Shuffler</summary>
  Na Máquina Virtual Shuffler:
  
```bash
  cd /opt
  git clone https://github.com/Shuffle/Shuffle
  cd Shuffle
  docker compose up -d
```

> 💡 **Nota:** Testado com a versão atual do Shuffle. Versões anteriores podem exigir ajuste manual de permissões no diretório `shuffle-database`.

</details>

<details>
  <summary>Instalando o DFIR-IRIS</summary>
  Na Máquina Virtual DFIR-IRIS:
  
```bash
  cd /opt
  git clone https://github.com/dfir-iris/iris-web.git
  cd iris-web
  git checkout v2.4.27
  cp .env.model .env
  docker compose up -d
```

  > ⚠️ **Aviso:** Para deploys em produção, edite o arquivo `.env` para configurar autenticação LDAP, SECRET KEY, SALT e credenciais do Postgres. Para fins de laboratório/testes, os valores padrão são suficientes.

  > 💡 **Nota:** `v2.4.27` era a versão mais recente no momento da escrita. Verifique a [página de releases](https://github.com/dfir-iris/iris-web/releases) para uma versão mais atualizada.

  Para recuperar a senha padrão do administrador:

```bash
  docker logs iriswebapp_app 2>&1 | grep 'create_safe_admin'
```

</details>