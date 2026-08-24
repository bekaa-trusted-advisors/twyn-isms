# SGP-NTP-001 — Sincronização de Relógios
**ISO/IEC 27001:2022 A.8.17**

---

**Controle de Documento**

| Campo | Valor |
|---|---|
| **Document ID** | SGP-NTP-001 |
| **Versão** | 1.0 (Rascunho) |
| **Elaborado por** | Consultoria Aegis (ENG-2026-001) |
| **A ser aprovado por** | Nizar Elouaer (CTO) |
| **Status** | `Rascunho — pendente de aprovação` |

---

## 1. Objetivo
Garantir a sincronização de relógios dos sistemas para permitir correlação confiável de logs e
evidências forenses.

## 2. Diretrizes
1. **Fonte de tempo:** todos os sistemas (EKS, instâncias, RDS) usam o Amazon Time Sync Service (NTP)
   como fonte única e confiável.
2. **Fuso:** registros em UTC para correlação; conversão apenas na apresentação.
3. **Verificação:** desvio de relógio monitorado; anomalias tratadas como evento (`A.6.8`).
4. **Dependência:** os registros de log (`A.8.15`) e a coleta de evidências (`A.5.28`) dependem desta
   sincronização.

## Aprovação

Documento em rascunho — pendente de aprovação. Nenhuma assinatura foi aposta por terceiros.

Aprovação: ______________________________  Data: ____ / ____ / ______
