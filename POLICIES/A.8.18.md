# SGP-PUP-001 — Uso de Programas Utilitários Privilegiados
**ISO/IEC 27001:2022 A.8.18**

---

**Controle de Documento**

| Campo | Valor |
|---|---|
| **Document ID** | SGP-PUP-001 |
| **Versão** | 1.0 (Rascunho) |
| **Elaborado por** | Consultoria Aegis (ENG-2026-001) |
| **A ser aprovado por** | Humberto Oliveira (CIO) · Nizar Elouaer (CTO) |
| **Status** | `Rascunho — pendente de aprovação` |

---

## 1. Objetivo
Restringir e controlar o uso de utilitários capazes de contornar controles de sistema e aplicação.

## 2. Diretrizes
1. **Restrição:** utilitários privilegiados (administração de RDS, acesso a nós EKS, ferramentas de
   sistema) restritos a perfis autorizados (`A.8.2` — acesso privilegiado).
2. **Acesso just-in-time:** elevação temporária e justificada, preferível a privilégio permanente.
3. **Registro:** uso de utilitários privilegiados é logado e auditável (`A.8.15`).
4. **Segregação:** separação entre quem solicita e quem aprova a elevação (`A.5.3`).

## Aprovação

Documento em rascunho — pendente de aprovação. Nenhuma assinatura foi aposta por terceiros.

Aprovação: ______________________________  Data: ____ / ____ / ______
