# SGP-TST-001 — Proteção de Informação de Teste
**ISO/IEC 27001:2022 A.8.33**

---

**Controle de Documento**

| Campo | Valor |
|---|---|
| **Document ID** | SGP-TST-001 |
| **Versão** | 1.0 (Rascunho) |
| **Elaborado por** | Consultoria Aegis (ENG-2026-001) |
| **A ser aprovado por** | Humberto Oliveira (CIO) · Nizar Elouaer (CTO) · Encarregado (DPO) |
| **Status** | `Rascunho — pendente de aprovação` |

---

> **Escopo (ENG-2026-001):** o TWYN mantém ambientes de desenvolvimento/homologação — controle
> **aplicável**.

## 1. Objetivo
Assegurar que dados usados em teste não exponham dados pessoais reais, em especial biometria.

## 2. Diretrizes
1. **Proibição de PII real:** é **vedado** usar imagens faciais ou vetores biométricos reais de
   titulares em ambientes de não produção.
2. **Dados sintéticos/mascarados:** testes usam dados sintéticos ou mascarados (`A.8.11`;
   `Diretrizes_Anonimizacao`).
3. **Controle de acesso e expurgo:** ambientes de teste têm acesso restrito e os dados são expurgados
   ao fim do uso (`POL-GOV-001` §4).
4. **Segregação:** produção e não produção segregadas.

## Aprovação

Documento em rascunho — pendente de aprovação. Nenhuma assinatura foi aposta por terceiros.

Aprovação: ______________________________  Data: ____ / ____ / ______
