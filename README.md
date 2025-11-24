Organizadores: 

André
Leticia
Luiza
Miguel

# Projeto Completo de Infraestrutura, Virtualização, Segurança e Portal Web (IIS)

Este repositório reúne **todo o projeto de infraestrutura** desenvolvido, incluindo:
- CASEMOD físico
- Dual boot (Windows 10 + Kali Linux)
- Máquina virtual com Windows Server
- Configurações de rede e acesso
- Segurança da Informação (DNS, VPN, firewall, antivírus, logs, backups)
- Publicação de site no IIS
- Exposição via Ngrok
- Portal de aplicações com mini-game em HTML/CSS/JS

Ele foi estruturado para uso em **apresentação de faculdade** e também como **portfólio profissional**.

---

## 🧱 Arquitetura Geral do Projeto

- **Máquina Física / CASEMOD**
  - Estrutura física personalizada em formato de palco de show.
  - Organização interna simulando um gabinete funcional.
  - Configuração de BIOS (ordem de boot, USB como prioridade).

- **Sistemas Operacionais**
  - **Windows 10 Pro**: sistema principal para uso diário e administração.
  - **Kali Linux**: utilizado para testes e práticas de segurança.

- **Dual Boot**
  - Particionamento do disco.
  - Instalação do Kali Linux via Ventoy.
  - GRUB configurado corretamente.
  - Espaço reservado para arquivos de máquina virtual.

- **Virtualização (VirtualBox)**
  - Criação de máquina virtual com **Windows Server**.
  - Servidor configurado para hospedar aplicações web (IIS).
  - Comunicação entre host e VM ajustada (NAT/Bridge).

---

## 🌐 Portal Web no IIS + Ngrok

O Windows Server hospeda um **portal de aplicações** acessível via navegador, composto pelos arquivos em `site/`:

- `index.html` – Página inicial do PortalAplicacoes.
- `status.html` – Página de status do sistema.
- `game.html` – Mini-game tipo Pong em JavaScript.
- `style.css` – Estilização do portal.

Esses arquivos foram publicados no IIS e expostos externamente usando **Ngrok**.

### Passos principais (resumo)
1. Copiar os arquivos da pasta `site/` para o diretório de publicação do IIS, por exemplo:
   ```text
   C:\inetpub\wwwroot\
   ```
2. Iniciar o IIS.
3. No Windows, abrir o PowerShell na pasta do Ngrok e executar:
   ```powershell
   cd C:\ngrok
   .\ngrok.exe config add-authtoken SEU_TOKEN_AQUI
   .\ngrok.exe http 8080
   ```
4. Utilizar o link gerado pelo Ngrok para acessar o portal de qualquer lugar.

Detalhes completos dos comandos utilizados estão no arquivo em `docs/passos_powershell.txt`.

---

## 🔐 Segurança da Informação

Os procedimentos de segurança foram documentados em `docs/seguranca_cyber.txt` e incluem:

- Configuração de **DNS seguro** (Cloudflare / Google).
- Instalação e uso de **VPN** (OpenVPN).
- Configuração de **firewall (UFW)** com política segura (deny incoming / allow outgoing).
- Criação de **senhas fortes** com `openssl rand`.
- Instalação e configuração de **antivírus (ClamAV)**.
- Ativação de **logs de segurança** (auditd).
- Configuração de **backups automáticos** (rsync + cron).
- Testes de vulnerabilidade com **Nmap** e ferramentas adicionais.

Esses passos mostram a preocupação com **confidencialidade, integridade e disponibilidade** dos serviços.

---

## 📂 Estrutura do Repositório

```text
projeto-infra-completo/
├── README.md
├── docs/
│   ├── projeto_full_stack_infra.pdf      # Documento do projeto completo
│   ├── passos_powershell.txt             # Comandos e passos no PowerShell (Ngrok, etc.)
│   └── seguranca_cyber.txt               # Script/guia de Segurança da Informação
└── site/
    ├── index.html                        # Página inicial do portal
    ├── status.html                       # Status do sistema
    ├── game.html                         # Mini-game em JS
    └── style.css                         # Estilos do portal
```

---

## 🚀 Como utilizar este repositório

1. **Clonar ou baixar** este repositório.
2. Importar ou abrir o PDF em `docs/projeto_full_stack_infra.pdf` para entender a documentação completa.
3. Usar os arquivos da pasta `site/` para hospedar no IIS ou outro servidor web.
4. Seguir os passos em `docs/passos_powershell.txt` para expor o serviço via Ngrok, se desejar.
5. Consultar `docs/seguranca_cyber.txt` para revisar e repetir as configurações de segurança em outro ambiente.

---

## 🎯 Objetivo

Este projeto demonstra, na prática:

- Montagem e organização de ambiente físico (CASEMOD).
- Configuração de dual boot entre Windows e Linux.
- Criação e administração de máquina virtual com Windows Server.
- Publicação de aplicações web com IIS.
- Exposição externa segura usando Ngrok.
- Aplicação de boas práticas de Segurança da Informação.
- Documentação técnica organizada e pronta para apresentação acadêmica e uso como portfólio.

Pode ser apresentado em banca de faculdade como um **projeto integrado de infraestrutura, redes e segurança**, além de servir como exemplo real de implementação para recrutadores e empresas.
