# SGP-CAP-001 — Gestão de Capacidade
**ISO/IEC 27001:2022 A.8.6**

---

**Controle de Documento**

| Campo | Valor |
|---|---|
| **Document ID** | SGP-CAP-001 |
| **Versão** | 1.0 (Rascunho) |
| **Elaborado por** | Consultoria Aegis (ENG-2026-001) |
| **A ser aprovado por** | Humberto Oliveira (CIO) · Nizar Elouaer (CTO) |
| **Status** | `Rascunho — pendente de aprovação` |

---

## 1. Objetivo
Assegurar que os recursos de TIC (compute, armazenamento, rede) sejam dimensionados para a demanda,
preservando disponibilidade e desempenho da API Face ID.

## 2. Diretrizes
1. **Monitoramento:** métricas de uso (CPU, memória, IOPS, conexões RDS, latência) via AWS CloudWatch
   e DataDog, com alarmes.
2. **Escalonamento:** autoscaling do cluster EKS e ajuste de capacidade do RDS conforme limiares.
3. **Planejamento:** revisão periódica de tendência de consumo e projeção de crescimento.
4. **Correlação com continuidade:** limites e planos de contingência alinhados a backup/DR
   (`POL-OPS-001`, `POL-GOV-001`).

## Aprovação

Documento em rascunho — pendente de aprovação. Nenhuma assinatura foi aposta por terceiros.

Aprovação: ______________________________  Data: ____ / ____ / ______
