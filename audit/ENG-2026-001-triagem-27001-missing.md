# Triagem — 28 controles ISO/IEC 27001 ainda `Missing` no nISO — issue #15

> **Documento de trabalho do consultor (ENG-2026-001).** Não é parecer de conformidade. Cada elevação
> de status no nISO depende de **aprovação humana**. Verificação final = auditoria 9.2 independente.

**Data:** 2026-08-24 · **Fonte:** nISO (`mr9c1qugo16zic2eko`), 93 controles 27001, **28 `Missing`**.

## Resumo

| Cat. | Qtd | Situação | Ação |
|---|---|---|---|
| **A2 — política já existe no repo** | 6 | Documento de suporte pronto | Elevar `Missing→Implemented` citando o doc (sob aprovação) |
| **B2 — evidência no store / export AWS** | 7 | #8 (re-vínculo UI) e #9 (export) | Ver `nISO-UI-tarefas-consolidado.md` A/E |
| **C2 — documento novo ou decisão** | 15 | Falta política/procedimento ou correção de aplicabilidade | Redigir em ondas / decisão |

---

## A2 — prontos para elevar (política existe) — 6

| Controle | Documento de lastro |
|---|---|
| A.5.25 — Avaliação/decisão sobre eventos | `POLICIES/A.5.25.md` (POL-IRP-001) |
| A.5.28 — Coleta de evidências | `POLICIES/A.5.28.md` (POL-IRP-001) |
| A.6.1 — Seleção de pessoas | `POLICIES/A.6.1.md` (POL-HR-001) |
| A.6.2 — Termos e condições de contratação | `POLICIES/A.6.2.md` (POL-HR-001) |
| A.6.4 — Processo disciplinar | `POLICIES/A.6.4.md` (POL-HR-001) |
| A.8.19 — Instalação de software | `POLICIES/A.8.19.md` (POL-CMP-001) |

## B2 — evidência existe, depende de UI/Ops (#8/#9) — 7

| Controle | id | Encaminhamento |
|---|---|---|
| A.8.8 — Vulnerabilidades | `ctrl-a88` | #8 — re-vincular pentest (UI) |
| A.8.11 — Mascaramento | `ctrl-a811` | #8 — re-vincular + corrigir aplicabilidade |
| A.8.12 — DLP | `ctrl-a812` | #9 — export AWS Macie + aplicabilidade |
| A.8.15 — Logs | `ctrl-a815` | #9 — export CloudTrail (+ política existe) |
| A.8.16 — Monitoramento | `ctrl-a816` | #9 — GuardDuty findings |
| A.8.23 — Filtragem web | `ctrl-a823` | #9 — export MDM **ou** decidir N/A (BYOD remoto) |
| A.8.29 — Testes de segurança | `ctrl-a829` | #8 — re-vincular DAST/SAST/pentest + aplicabilidade |

## C2 — precisa de documento novo ou decisão — 15

**Correção de aplicabilidade (seed errado):**
- A.5.23 (nuvem), A.6.7 (trabalho remoto) → **aplicáveis** + política (ver consolidado B).

**Documento/procedimento novo a redigir (ondas):**
- A.5.27 — Aprendizado com incidentes (pode estender POL-IRP-001).
- A.5.32 — Direitos de propriedade intelectual.
- A.5.36 — Verificação de conformidade (com políticas/normas).
- A.5.37 — Procedimentos operacionais documentados.
- A.6.8 — Notificação de eventos (pode estender POL-IRP-001).
- A.8.1 — Dispositivos de usuário final (endpoint).
- A.8.6 — Gestão de capacidade.
- A.8.7 — Proteção contra malware.
- A.8.17 — Sincronização de relógio (NTP).
- A.8.18 — Uso de utilitários privilegiados.
- A.8.33 — Informação de teste (verificar se aplicável; possível N/A).
- A.8.34 — Proteção de sistemas durante auditoria.

**Não é do consultor:**
- **A.5.35 — Análise crítica independente** = a própria **auditoria interna 9.2** (issue #17), por
  parte independente. Não pode ser executada por quem implementa.

---

## Recomendação de sequência

1. **Aprovar A2 (6):** elevo no nISO com lastro citado → 27001 Missing 28 → 22.
2. **B2 (7):** consolidado de UI/Ops (#8/#9) — não é escrita de API.
3. **C2 (12 documentais):** redijo em ondas (começando por reaproveitar POL-IRP-001 para A.5.27/A.6.8
   e políticas curtas para A.8.7/A.8.17/A.8.1); A.5.23/A.6.7 saem com correção de aplicabilidade.
4. **A.5.35:** encaminhar ao #17 (auditoria independente).
