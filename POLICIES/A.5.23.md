# POL-CLD-001 — Uso Seguro de Serviços em Nuvem
**ISO/IEC 27001:2022 A.5.23 | ISO/IEC 27701:2025**

---

**Controle de Documento**

| Campo | Valor |
|---|---|
| **Document ID** | POL-CLD-001 |
| **Versão** | 1.0 (Rascunho) |
| **Elaborado por** | Consultoria Aegis (ENG-2026-001) |
| **A ser aprovado por** | Humberto Oliveira (CIO) · Kacio Giuliano Lopes (CEO) |
| **Status** | `Rascunho — pendente de aprovação` |

---

> **Correção de escopo (ENG-2026-001):** o registro anterior indicava "nenhum serviço em nuvem
> identificado", o que é **incorreto** — 100% da infraestrutura do TWYN opera na **AWS** (`sa-east-1`).
> Controle **aplicável**.

## 1. Objetivo
Definir os requisitos para aquisição, uso e gestão seguros de serviços em nuvem (AWS), sob o modelo de
responsabilidade compartilhada.

## 2. Diretrizes
1. **Responsabilidade compartilhada:** a AWS responde pela segurança *da* nuvem; o TWYN pela segurança
   *na* nuvem (config, IAM, dados). Ver `A.5.19`/`A.5.22` (fornecedor) e SOC/ISO da AWS (EVIDENCE).
2. **Configuração segura:** baselines de EKS, RDS, S3 (Block Public Access), Security Groups/VPC;
   AWS Config e GuardDuty ativos (ver `A.8.9`, `A.8.16`).
3. **Criptografia:** dados em repouso via KMS (AES-256) e em trânsito TLS 1.3 (ver `A.8.24`, `ROPA.md`).
4. **Identidade e acesso:** IAM com menor privilégio, MFA e revisão periódica (ver `A.5.15`–`A.5.18`).
5. **Contratos/DPA:** termos AWS e adendo de proteção de dados aplicáveis (ver `A.5.34`).
6. **Localização:** produção em `sa-east-1` (São Paulo, **Brasil**) — os dados pessoais permanecem em
   **território nacional**; **não há transferência internacional** (ver `ROPA.md`).

## Aprovação

Documento em rascunho — pendente de aprovação. Nenhuma assinatura foi aposta por terceiros.

Aprovação: ______________________________  Data: ____ / ____ / ______
