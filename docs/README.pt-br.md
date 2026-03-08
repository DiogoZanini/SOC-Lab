# SOC Lab
Laboratório de Centro de Operações de Segurança para prática hands-on com SIEM, análise de logs, detecção de ameaças e fluxos de resposta a incidentes.

## 📦 Dependências
- [Oracle VirtualBox](https://www.virtualbox.org/) — Plataforma de virtualização;
- [Ubuntu Desktop](https://ubuntu.com/download/desktop) — Sistema operacional base para o ambiente do laboratório.
- [Docker](https://docs.docker.com/engine/install/ubuntu/) — Plataforma de contêineres para executar componentes do SOC.

## 🚀 Primeiros Passos
<details>
  <summary>Configuração da Máquina Virtual</summary>

  - Memória Base: 8192 MB (8 GB);
  - Número de CPUs: 4 CPUs;
  - Tamanho do Disco: 25 GB;
  - Adaptador de Rede: NAT (para acesso à internet durante a configuração).

  > 💡 **Observação:** Essas especificações podem ser ajustadas com base nos recursos da sua máquina host e requisitos do laboratório.

</details>

<details>
  <summary> Instalando o Docker</summary>
```bash
  curl https://get.docker.com | bash
```

</details>

<details>
  <summary> Clonando a VM para o DFIR-IRIS</summary>

  No VirtualBox, clique com o botão direito na VM principal → **Clonar**:
  - Nome: `DFIR-IRIS`
  - Tipo de clone: **Clone completo**

  > 💡 **Nota:** Clonar evita reinstalar o sistema operacional e o Docker do zero.

</details>