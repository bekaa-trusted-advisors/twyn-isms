# SOP-ARC-001: Manual de Arquitetura e Engenharia Segura — TWYN Face ID Platform
**ISO/IEC 27001:2022 Controles A.8.14 (Redundância de facilidades de processamento de informação) e A.8.27 (Princípios de engenharia de sistemas seguros)**

---

**Controle de Documento**

| Campo | Valor |
|-------|-------|
| **Document ID** | SOP-ARC-001 |
| **Version** | 1.0 (Oficial) |
| **Autor** | Nizar Elouaer (CTO) |
| **Aprovador** | Nizar Elouaer (CTO) |
| **Data de Emissão** | 16/07/2026 |
| **Status** | `Aprovado` |

---

## 1. Objetivo

Documentar os princípios de engenharia e a arquitetura redundante adotados na TWYN Face ID Platform para mitigar pontos únicos de falha (SPOF) e garantir o processamento seguro de dados biométricos.

---

## 2. Princípios de Engenharia de Sistemas Seguros (A.8.27)

1.  **Arquitetura Zero Trust nas APIs:** Toda requisição ou comunicação inter-microsserviços no cluster deve ser tratada como hostil por padrão, exigindo autenticação do token JWT correspondente e validação lógica.
2.  **Segregação Lógica de Dados Biométricos:**
    *   Dados cadastrais dos clientes B2B e logs gerais são armazenados em tabelas de controle separadas.
    *   Hashes biométricos (templates faciais) são armazenados em base isolada sem dados identificadores diretos, associados exclusivamente através de chaves UUID pseudoanônimas de mão única.
3.  **Configuração Padrão Segura (Secure by Default):** Todo provisionamento via Terraform deve adotar privilégio mínimo por padrão, com portas fechadas e negação explícita nas políticas do AWS IAM e Security Groups.

---

## 3. Redundância e Alta Disponibilidade (A.8.14)

1.  **Cluster EKS Multi-AZ:** Os microsserviços da API operam em nós do cluster Amazon EKS distribuídos de forma homogênea em no mínimo 3 Zonas de Disponibilidade (Availability Zones) na AWS.
2.  **Banco de Dados RDS Multi-AZ:** O RDS Aurora PostgreSQL opera com uma réplica de leitura síncrona habilitada em Zona de Disponibilidade distinta. O failover do endpoint de escrita é automático e gerenciado pela AWS em caso de colapso físico do nó primário.

---

## 4. Revisão e Aprovação

Esta política é aprovada pela Liderança Técnica da TWYN e revisada anualmente.

**Nizar Elouaer**  
CTO / Liderança de SI  
TWYN T4ISB DO BRASIL TECNOLOGIA E PARTICIPACOES LTDA (CNPJ: 31.122.819/0001-55)
*Assinado eletronicamente via TWYN GRC Portal em 21/07/2026 18:00 BRT (IP: 191.189.44.112, Hash: cbe35f785e2e4f6283fbf5a4b14e7073)*
