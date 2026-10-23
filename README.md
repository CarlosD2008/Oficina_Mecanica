<div align="center">

<!-- Header SVG Animado / Banner -->
<img src="https://capsule-render.vercel.app/api?type=waving&color=3776AB&height=200&section=header&text=AutoMec%C3%A2nica%20Pro&fontSize=50&fontColor=ffffff&animation=twinkle" width="100%" alt="Header Oficina Mecânica"/>

<!-- Efeito de Digitação Animado -->
<a href="https://github.com/readme-typing-svg">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&pause=1000&color=3776AB&center=true&vcenter=true&width=600&lines=Gest%C3%A3o+Integrada+para+Oficinas+Mec%C3%A2nicas;Dashboard+com+Indicadores+em+Tempo+Real;Controle+Completo+de+Ordens+de+Servi%C3%A7o;Projeto+Acad%C3%AAmico+SAEP+-+SENAI" alt="Typing SVG" />
</a>

<br><br>

<!-- Badges do Projeto -->
<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Flask-3.0.3-000000?style=for-the-badge&logo=flask&logoColor=white" alt="Flask">
  <img src="https://img.shields.io/badge/MySQL-8.0-4479A1?style=for-the-badge&logo=mysql&logoColor=white" alt="MySQL">
  <img src="https://img.shields.io/badge/JavaScript-ES6+-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript">
  <img src="https://img.shields.io/badge/SAEP-SENAI-D92938?style=for-the-badge" alt="SAEP SENAI">
</p>

<p align="center">
  <b>Aplicação Web completa para centralização, automação e gerenciamento de clientes, veículos e ordens de serviços automotivos.</b>
</p>

---

[📌 Funcionalidades](#-funcionalidades-principais) •
[🛠️ Tecnologias](#️-tecnologias--bibliotecas) •
[🏗️ Arquitetura](#️-arquitetura-do-sistema) •
[🗄️ Banco de Dados](#️-modelo-do-banco-de-dados-saep_db) •
[🚀 Instalação](#-instalação-e-execução) •
[🛣️ Rotas API](#️-rotas-principais)

</div>

<br>

---

## 📌 Funcionalidades Principais

| Módulo | Descrição / Recursos | Status |
| :--- | :--- | :---: |
| 📊 **Dashboard Interativo** | Painel em tempo real com métricas key-value (total de clientes, veículos cadastrados) e feed dos próximos serviços agendados. | <kbd>🟢 Ativo</kbd> |
| 👥 **Gestão de Clientes** | Cadastro, edição e busca dinâmica em tempo real (por CPF, Nome ou E-mail) com tratamento/hash de segurança de dados sensíveis. | <kbd>🟢 Ativo</kbd> |
| 🚗 **Gestão de Veículos** | Registro e associação direta de veículos (Placa, Modelo, Marca, Ano) aos seus respectivos proprietários. | <kbd>🟢 Ativo</kbd> |
| 📅 **Agendamentos & O.S.** | Fluxo de Ordem de Serviço com pipeline visual de status (`Agendado` ➔ `Em Andamento` ➔ `Concluído` ➔ `Cancelado`). | <kbd>🟢 Ativo</kbd> |
| 🔐 **Autenticação & Segurança** | Tela de login, gerenciamento de sessão com expiração automática e segurança de senhas via criptografia hash Bcrypt. | <kbd>🟢 Ativo</kbd> |

<br>

---

## 🛠️ Tecnologias & Bibliotecas

<details open>
<summary><b>🔍 Clique para expandir a Stack Técnica</b></summary>

<br>

- **Back-End:**
  - `Python 3`: Linguagem base da aplicação.
  - `Flask 3.0.3`: Microframework web para rotas, Jinja2 templating e gerenciamento de contexto/sessão.
  - `Flask-Bcrypt` / `Bcrypt`: Criptografia e validação de hashes de senhas.
  - `mysql-connector-python`: Driver nativo de comunicação com o MySQL.

- **Front-End:**
  - `HTML5 / CSS3`: Estilização responsiva, layout modular e design adaptável.
  - `JavaScript (ES6+)`: Modais dinâmicos, validação de formulários no client-side e requisições assíncronas.
  - `Jinja2`: Renderização dinâmica de templates server-side.

- **Banco de Dados:**
  - `MySQL`: SGBD relacional para armazenamento de dados da aplicação (`saep_db`).

</details>

<br>

---

## 🏗️ Arquitetura do Sistema

```mermaid
flowchart TD
    classDef client fill:#1e293b,stroke:#38bdf8,stroke-width:2px,color:#fff;
    classDef server fill:#0f172a,stroke:#3776ab,stroke-width:2px,color:#fff;
    classDef db fill:#064e3b,stroke:#10b981,stroke-width:2px,color:#fff;
    classDef sec fill:#581c87,stroke:#c084fc,stroke-width:2px,color:#fff;

    subgraph FrontEnd ["💻 Front-End (Navegador)"]
        A["🎨 Modais & Interface HTML5/CSS3"]:::client
        B["⚡ JavaScript Asynchronous / Eventos"]:::client
    end

    subgraph BackEnd ["🚀 Back-End (Flask Server)"]
        C["🌐 Rotas & Controllers (app.py / rotas.py)"]:::server
        D["🔒 Autenticação & Expiração de Sessão"]:::sec
        E["📊 CRUD Engine (Clientes / Veículos / Agendamentos)"]:::server
    end

    subgraph DataLayer ["🗄️ Camada de Dados"]
        F[("🛢️ MySQL Server (saep_db)")]:::db
    end

    A <--> B
    B -- "Requisições HTTP / Forms" --> C
    C --> D
    C --> E
    D -- "Validação Hash Bcrypt" --> F
    E -- "Query SQL (mysql-connector)" --> F
