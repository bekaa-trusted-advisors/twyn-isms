# SOP-HDN-001: Manual de Configuração Segura (Hardening) — TWYN Face ID Platform
**ISO/IEC 27001:2022 Controle A.8.9 (Gerenciamento de configuração)**

---

**Controle de Documento**

| Campo | Valor |
|-------|-------|
| **Document ID** | SOP-HDN-001 |
| **Version** | 1.0 (Oficial) |
| **Autor** | Marcelo Mascarenhas (DevOps) |
| **Aprovador** | Nizar Elouaer (CTO) |
| **Data de Emissão** | 16/07/2026 |
| **Status** | Aprovado |

---

## 1. Objetivo

Estabelecer os padrões mínimos de configuração segura (hardening) para os ativos de processamento hospedados na nuvem AWS correspondentes à Face ID Platform.

---

## 2. Hardening de Servidores e Nós (EC2/EKS)

1.  **Imagens Mínimas:** Instâncias EC2 e nós do cluster Kubernetes (EKS) devem utilizar imagens oficiais mínimas e otimizadas para contêineres (ex: Bottlerocket ou Amazon Linux Minimal), desprovidas de compilers ou shells administrativos desnecessários.
2.  **Portas de Acesso Bloqueadas:** Fica proibida a exposição pública de portas de gerenciamento (SSH/22 ou RDP/3389). Toda gerência remota administrativa deve trafegar exclusivamente pela VPN corporativa privada.
3.  **Configurações de Baseline:** O time de DevOps deve auditar mensalmente a conformidade das instâncias AWS contra os baselines de segurança do CIS (Center for Internet Security) Benchmarks.

---

## 3. Hardening do Banco de Dados (RDS Aurora PostgreSQL)

1.  **Acesso Não-Público:** A propriedade `Publicly Accessible` nas configurações do RDS Aurora deve estar ativada no valor `False` (banco de dados isolado em sub-rede sem acesso externo).
2.  **Criptografia Integrada:** A base de dados de produção do RDS e seus snapshots devem possuir criptografia AES-256 habilitada baseada em chave mestra exclusiva criada no AWS KMS.
3.  **Logs de Auditoria:** Habilitar e exportar os logs PostgreSQL detalhados (logs de conexões e queries DDL) para o Amazon CloudWatch Logs, com monitoramento ativo.

---

## 4. Revisão e Aprovação

Esta política é aprovada pela Liderança Técnica da TWYN e revisada anualmente.

**Nizar Elouaer**  
CTO / Liderança de SI  
TWYN T4ISB DO BRASIL TECNOLOGIA E PARTICIPACOES LTDA (CNPJ: 31.122.819/0001-55)
*Assinado eletronicamente via TWYN GRC Portal em 21/07/2026 18:00 BRT (IP: 191.189.44.112, Hash: f60dc8949feec94f2381bde99796404e)*
