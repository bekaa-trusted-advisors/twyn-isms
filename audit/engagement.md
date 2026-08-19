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
| Estado da key nesta sessão | ⛔ **UNSET** em 2026-08-18 — aguardando injeção humana |

> **Regra de escrita:** toda mutação no nISO segue **PROPOSTA → aprovação humana → aplicação**,
> uma aprovação por vez. Nenhuma escrita antes de reads de verificação (ver
> `audit/C-2026-08-18-01-migration-27701-2025.md`).

## Baseline de migração (snapshot-first) — a capturar no 1º GET

> `db:backup` no nISO já realizado (informado pelo cliente). Baseline a registrar a partir das
> respostas dos endpoints read, para permitir **rollback parcial**.

| Fonte | Baseline | Como capturar |
|---|---|---|
| **Repo (âncora git)** | `main @ 6697267` (SoA/README/RISKS pré-reconciliação) | congelado no histórico |
| **nISO — standards** | `27701:2019` (reportado) | `GET /projects/:id` |
| **nISO — status/prontidão** | `Audit Ready` (reportado) | `GET /projects/:id/readiness-check` |
| **nISO — SoA/controles** | _pendente_ | `GET /controls?project_id=:id` |
| **nISO — ROPA** | _pendente_ | `GET /projects/:id/ropa` |
| **nISO — evidências** | _pendente_ | `GET /projects/:id/evidence` |

*(As linhas "pendente" serão preenchidas com o retrato :2019 assim que a key for injetada.)*

## Journal

| Data | Evento |
|---|---|
| 2026-08-18 | Reconciliação de prontidão (PR #2): IPC recalculado (~66%), inconsistências do SoA sinalizadas, 3 riscos reabertos, esqueleto SGPI 27701:2025. |
| 2026-08-18 | Contrato **C-2026-08-18-01** registrado (Entregável #1 = migração 27701:2019→2025). Acesso nISO definido via HTTP API. Key UNSET — parado para injeção humana. |
