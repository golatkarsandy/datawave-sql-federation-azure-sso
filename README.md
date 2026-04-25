# Datawave SQL Federation — Trino + Azure AD SSO + Metabase

This project demonstrates a secure, production‑ready setup of **Trino** with:

- Azure Active Directory OAuth2 SSO for the Trino Web UI  
- HTTPS enabled using a Java Keystore  
- Password authentication for JDBC clients (Metabase)  
- Federated SQL queries across PostgreSQL and MySQL  
- Metabase as the BI layer connecting to Trino over SSL  

This repository is the **SSO‑enabled version** of the project.

---

## 🚀 Architecture Overview

```mermaid
flowchart LR
    User((User Browser)) -->|Login Redirect| AzureAD((Azure AD))
    AzureAD -->|OAuth2 Token| TrinoUI[Trino Web UI (HTTPS + SSO)]

    Metabase -->|JDBC + Password Auth| TrinoEngine[Trino Engine]
    TrinoEngine --> MySQL[(MySQL)]
    TrinoEngine --> Postgres[(PostgreSQL)]
