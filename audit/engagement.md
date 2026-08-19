# Engagement Workspace — ENG-2026-001

| Campo | Valor |
|---|---|
| **Código (anonimizado)** | **ENG-2026-001** — *nunca* "ENG-twyn" no registry |
| **Cliente / projeto** | TWYN — Face ID Platform |
| **nISO project_id** | `mr9c1qugo16zic2eko` |
| **Repo ISMS** | `bekaa-trusted-advisors/twyn-isms` |
| **Modo** | CONSULTOR (implementa e adequa) |
| **Escopo normativo** | ISO/IEC 27001:2022 (SGSI) + ISO/IEC 27701:2025 (SGPI) |
| **Aprovador humano** | resper@bekaa.eu |
| **Aberto em** | 2026-08-18 |

## Contratos

| Contrato | Data | Modo | Escopo | Entregável | Status |
|---|---|---|---|---|---|
| **C-2026-08-18-01** | 2026-08-18 | Consultor | 27001:2022 + 27701:2025 | **#1 — Migração SGPI 27701:2019 → 2025** (com rollback parcial) | `Ativo` |

## Acesso ao nISO (fonte da verdade = D1)

| Item | Valor |
|---|---|
| Método | **HTTP API** (mesmo backend do mcp-server; clone cross-tier abandonado) |
| Base URL | `https://niso.ness.workers.dev` |
| Auth | header `X-API-Key: <NISO_API_KEY>` — **SECRET de sessão**, nunca em chat/git |
| Papel | `consultant` · `NISO_READONLY=false` (write) |
| Isolamento | chave presa ao projeto `mr9c1qugo16zic2eko` no backend (não alcança outro projeto) |
| Estado da key nesta sessão | ✅ ativa (write; fora do repo, scratchpad 600) — conexão 5/5 HTTP 200. Cliente rotaciona `mcp-key-1` em 2026-08-19 |

> **Regra de escrita:** toda mutação no nISO segue **PROPOSTA → aprovação humana → aplicação**,
> uma aprovação por vez. Nenhuma escrita antes de reads de verificação (ver
> `audit/C-2026-08-18-01-migration-27701-2025.md`).

## Baseline de migração (snapshot-first) — capturado do nISO em 2026-08-19

> Retrato `:2019` lido da fonte da verdade (nISO D1) para permitir **rollback parcial**.
> `db:backup` do backend já realizado (informado pelo cliente) = rollback total.
> Verificação de conexão: **5/5 endpoints read HTTP 200**.

| Fonte | Baseline capturado |
|---|---|
| **Repo (âncora git)** | `main @ 6697267` (SoA/README/RISKS pré-reconciliação) |
| **nISO — project** | `TWYN Face ID Platform` · org_role `Controller` · lang `pt-BR` |
| **nISO — standards** | **ISO 27001:2022, ISO 27701:2019** |
| **nISO — status** | **`Audit Ready`** |
| **nISO — readiness (auto-diagnóstico)** | **66 achados — 17 críticos · 0 altos · 49 médios** (gerado 2026-08-19T01:11:33Z; rótulo: "não é auditoria nem parecer") |
| **nISO — controles (93)** | **0 Implemented · 69 Missing · 6 In Progress · 2 Planned · 16 Not Applicable** |
| **nISO — maturidade** | CMM: 0→36 · 2→4 · 3→28 · 4→21 · 5→4 |
| **nISO — ROPA** | 1 registro (Controller; base legal LGPD Art. 11 II g) |
| **nISO — evidências** | **124 itens** (r2_key + file_hash + evaluation_status) |

### ⚠ Divergência material repo × fonte da verdade (registrar como achado)

O `SOA.md` do repo declarava `49 Implemented / IPC 100% / Audit Ready`; a **fonte da verdade (nISO)**
mostra **0 Implemented, 69 Missing** e um auto-diagnóstico com **17 achados críticos**. O status
`Audit Ready` é contraditado pelo próprio nISO. Isso reforça a reconciliação (PR #2) e **justifica a
Fase 2 da migração** (status `Audit Ready → In Progress`). Snapshots brutos preservados fora do repo
(scratchpad): `niso_project/controls/readiness/ropa/evidence.json`.

## Journal

| Data | Evento |
|---|---|
| 2026-08-18 | Reconciliação de prontidão (PR #2): IPC recalculado (~66%), inconsistências do SoA sinalizadas, 3 riscos reabertos, esqueleto SGPI 27701:2025. |
| 2026-08-18 | Contrato **C-2026-08-18-01** registrado (Entregável #1 = migração 27701:2019→2025). Acesso nISO definido via HTTP API. Key UNSET — parado para injeção humana. |
| 2026-08-19 | Key injetada; conexão nISO verificada (5/5 HTTP 200). Baseline `:2019` capturado. Divergência material repo × nISO registrada (nISO: 0 Implemented/69 Missing/17 críticos vs. repo "IPC 100%"). Próximo: propor Fase 2 (status → In Progress) para aprovação. |
