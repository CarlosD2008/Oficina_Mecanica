<div align="center">

# 🔧 AutoMecânica Pro
**Sistema de Gestão Integrada para Oficina Mecânica**

<p align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Flask-3.0.3-000000?style=for-the-badge&logo=flask&logoColor=white" alt="Flask">
  <img src="https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white" alt="MySQL">
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript">
</p>

<p>Aplicação web acadêmica (SAEP-SENAI) para centralizar e gerenciar clientes, veículos e agendamentos de serviços automotivos.</p>

</div>

---

## 🚀 Funcionalidades

- 📊 **Dashboard:** Indicadores em tempo real (total de clientes, veículos e lista de próximos serviços).
- 👥 **Gestão de Clientes:** Cadastro, edição, busca dinâmica (CPF, nome, e-mail) e hash de CPF.
- 🚗 **Gestão de Veículos:** Cadastro de veículos vinculados aos respectivos proprietários.
- 📅 **Agendamentos:** Controle de ordem de serviço por status (*Agendado*, *Em Andamento*, *Concluído*, *Cancelado*).
- 🔐 **Autenticação Segura:** Sistema de login com tempo de expiração de sessão e criptografia via Bcrypt.

---

## 🛠️ Tecnologias

| Tecnologia | Aplicação no Projeto |
| :--- | :--- |
| **Python 3 & Flask** | Lógica de back-end, roteamento e gestão de sessões |
| **MySQL** | Banco de dados relacional (via `mysql-connector-python`) |
| **Bcrypt** | Criptografia e verificação de senhas de acesso |
| **HTML5 / CSS3 / JS** | Front-end dinâmico com modais e templates Jinja2 |

---

## 🏗️ Arquitetura e Estrutura

```mermaid
flowchart TD
    A[Interface HTML/CSS/JS] --> B[Flask: app.py / rotas.py]
    B --> C[Autenticação]
    B --> D[Clientes / Veículos / Agendamentos]
    C --> E[(MySQL: saep_db)]
    D --> E
