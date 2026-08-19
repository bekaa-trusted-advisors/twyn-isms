# Resultados da Execução P0 — ENG-2026-001

| Campo | Valor |
|---|---|
| Data | 2026-08-19 |
| Aprovação | "tudo aprovado" (humano) |
| Fonte da verdade | nISO (`mr9c1qugo16zic2eko`) |

## Resultado quantitativo (antes → depois)

| Métrica | Antes | Depois |
|---|---|---|
| Readiness — total de achados | 66 | **25** |
| — críticos | 17 | 17 |
| — médios | 49 | **8** |
| Controles 27001 `Missing` | 69 | **28** |
| Controles 27001 `In Progress` | 6 | **47** |
| `Missing` com maturidade >0 (incoerência) | 48 | **7** |

## O que foi aplicado (P0-A) ✅

- **41 controles** `Missing` (com maturidade e evidência) → **`In Progress`**, via `PUT /controls/{id}`,
  cada um verificado. Corrigiu a maior parte da incoerência status × maturidade.
- Nenhum controle elevado a `Implemented` (isso exige evidência verificada — P1).

## Constatações técnicas da API (limites descobertos)

> Escritas de controle via `PUT /api/v1/controls/{id}` aceitam **apenas `status` e `description`**.
> Os demais campos são **imutáveis** por esta rota:

- **`maturity` não é gravável** (derivado). Logo os **7** controles `Missing` com maturidade alta e
  **sem evidência** (A.8.8/8.11/8.12/8.15/8.16/8.23/8.29) não puderam ter a maturidade zerada por API.
- **Campos de aprovação** (`ciso_approved_by`/`ceo_approved_by`/…) **não são graváveis** (o `null` é
  ignorado). Logo a "retirada de aprovação" (P0-B) **não é executável por API** — é ação de governança.

## Itens que permanecem — exigem governança/decisão humana (não fabricáveis)

| Item | NC | Por quê não automatizei |
|---|---|---|
| **17 "assinatura sem lastro"** (críticos) | NC-02 | Só se resolve por (a) **upload de evidência** objetiva, ou (b) **retirada da aprovação no UI do nISO**. API não permite; e não invento evidência. |
| **7 `Missing` maturidade alta sem evidência** | NC-01 | `maturity` imutável por API; alternativa é coletar evidência (P1) ou ajuste no backend. |
| **42 evidências `pending`** | NC-05 | Avaliar conformidade é **julgamento** — não estampo `conforme` sem análise real (seria fabricar). |
| **7 evidências órfãs + casing** | NC-05 | Requer endpoint de escrita de evidência (a descobrir) + decisão de religar/remover. |
| **28 controles 27701 aplicáveis** | NC-04 | Adequação P1, controle a controle, com evidência verificada. |
| **Retirada de aprovação (13 Missing assinados)** | NC-02 | Registro de assinatura de executivos nomeados — ação de governança no UI. |

## Recomendação

O P0-A restaurou a maior parte da integridade (readiness 66→25). Os itens restantes **não são
adiáveis por serem menos importantes** — são **críticos** —, mas dependem de **ação humana/governança**
(evidência real, decisões no UI do nISO) e **não podem ser fabricados**. Próximo bloco natural: coletar/
anexar evidência para os 17 críticos e iniciar a implementação (P1), sempre sob aprovação.

> **Independência:** verificação final (9.2) por sessão/agente independente.
