# POL-MAL-001 — Proteção contra Código Malicioso (Malware)
**ISO/IEC 27001:2022 A.8.7**

---

**Controle de Documento**

| Campo | Valor |
|---|---|
| **Document ID** | POL-MAL-001 |
| **Versão** | 1.0 (Rascunho) |
| **Elaborado por** | Consultoria Aegis (ENG-2026-001) |
| **A ser aprovado por** | Humberto Oliveira (CIO) · Nizar Elouaer (CTO) |
| **Status** | `Rascunho — pendente de aprovação` |

---

## 1. Objetivo
Prevenir, detectar e responder a código malicioso nos endpoints e na infraestrutura da plataforma.

## 2. Diretrizes
1. **Endpoints:** antimalware ativo, atualizado e monitorado em todos os dispositivos (`A.8.1`).
2. **Contêineres/EKS:** varredura de imagens de container por vulnerabilidades/malware no pipeline
   antes do deploy; imagens de base confiáveis.
3. **Nuvem:** detecção de ameaças com AWS GuardDuty (`A.8.16`); resposta pelo CSIRT (`POL-IRP-001`).
4. **Conscientização:** orientação anti-phishing e sobre execução de software não confiável (`A.6.3`).

## Aprovação

Documento em rascunho — pendente de aprovação. Nenhuma assinatura foi aposta por terceiros.

Aprovação: ______________________________  Data: ____ / ____ / ______
