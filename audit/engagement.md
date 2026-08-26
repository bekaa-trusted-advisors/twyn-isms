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

### Capacidades da API do papel `consultant` — o que É executável AQUI (fonte autoritativa)

> ⚠️ **Correção de 2026-08-25:** entradas antigas do journal (2026-08-19) afirmaram que
> "a API não re-vincula evidência (é ação de UI)". **Isso está ERRADO.** A re-vinculação
> **é executável pelo consultor via API** — verificado e aplicado nesta data.

| Ação | Executável pela API do consultor? | Verbo / contrato |
|---|---|---|
| **Re-vincular evidência a controle** | ✅ **SIM** | `PUT /api/v1/evidence/{id}` · body `{"control_id":"<id>"}` (ou `null` p/ desassociar) → `{"ok":true,"relinked":true}` |
| Alterar **status** do controle | ✅ SIM | `PUT /api/v1/controls/{id}` · body `{"status":"..."}` (Missing/In Progress/Implemented/Planned/Not Applicable) |
| Editar **descrição/justificativa** do controle | ✅ SIM (⚠ efeito colateral: **limpa `ciso_approved_by`**) | `PUT /api/v1/controls/{id}` · `{"description":"..."}` |
| Alterar **`owner`** do controle | ✅ **SIM** (liberado pelo nISO em 2026-08-26) | `PUT /api/v1/controls/{id}` · `{"owner":"..."}` → `{"ok":true}` |
| Alterar **aplicabilidade/flag N/A** (fora do status) | ❌ NÃO (só UI/admin) | — |
| **Aprovar** evidência/controle (`ciso_/ceo_approved_*`) | ❌ NÃO por PUT genérico | `/approve` exige `password`; retirada de aprovação = editar description (limpa o campo) |
| Alterar `maturity` | ❌ NÃO (imutável por API) | — |

**Notas operacionais de acesso:**
- **Auth = header `X-API-Key`** (NÃO `Authorization: Bearer` nem `X-Session-ID` → esses dão 401).
- **Cloudflare bloqueia `python-urllib` (cf-1010 / HTTP 403).** Usar **`curl`** para mutações
  (ou setar `User-Agent` no urllib). GET pelo mesmo motivo: preferir curl.
- **Status NÃO recalcula sozinho** ao vincular evidência — anexar a evidência e **elevar o status**
  são dois PUTs distintos.
- **Quem declara o status é a organização/consultoria** (inclusive **`Implemented`**), com base em
  **evidência objetiva citável**. O **auditor NÃO decide o status — ele REVISA o resultado** (9.2 +
  certificação verificam se a asserção se sustenta). Ou seja, marcar `Implemented` quando há evidência
  de que o controle está implementado **não** usurpa a auditoria; a independência é preservada porque
  a revisão é feita por parte independente **depois**.
- **NEVER que permanece:** nunca declarar `Implemented`/conforme **sem evidência citável**. Onde a
  evidência é **parcial** (ex.: um pentest não cobre todo o A.8.8 de gestão de vulnerabilidades), o
  honesto é `In Progress` até a evidência completar — não por deferência ao auditor, mas por falta de
  lastro.

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
| 2026-08-19 | **Escrita nISO #1 APLICADA** (aprovada): `project.status` `Audit Ready` → `In Progress`. Verbo de escrita = `PUT /projects/:id` (PATCH → 404). Verificado por GET. Reversível (db:backup). |
| 2026-08-19 | **Escrita nISO #2** (standards→2025): **no-op** — API `Nothing to update` (campo não editável via PUT). Descoberta: **0 controles 27701 no nISO** (93 são 27001:2022). Migração reenquadrada: criar control-set 27701:2025. Aguardando mecanismo do cliente. |
| 2026-08-19 | **Escrita nISO #3 APLICADA** (`POST seed-27701-2025`): criados **31 controles 27701:2025** (Controller), todos `Missing`; 27001:2022 preservado (93); `standards`→`27701:2025`. Controles 93→124. Catálogo espelhado em `soa/SGPI-SoA-27701-2025.md`. |
| 2026-08-19 | **Escritas nISO #4–6 APLICADAS** (lote aplicabilidade, aprovado): A.1.2.4/A.1.2.5/A.1.3.5 → `Not Applicable` + justificativa (base Art. 11 II g). Verbo `PUT /controls/{id}` (justificativa=`description`). 27701 = 28 Missing / 3 N/A. |
| 2026-08-19 | **Execução P0 (aprovada)**: 41 controles `Missing→In Progress` aplicados no nISO. Readiness **66→25 achados** (médios 49→8). Constatado: `maturity` e aprovações **imutáveis por API** → 17 críticos e retirada de aprovação viram ação de governança. Ver `audit/ENG-2026-001-P0-execution-results.md`. |
| 2026-08-19 | **#14 avançado**: descrição de adequação + evidência candidata gravada nos **28 controles 27701:2025** aplicáveis (nISO), status mantido `Missing` (sem fabricar conformidade). Norma oficial recebida (ABNT NBR 27701:2026) → índice de referência + crosswalk confirmados; cabeçalhos de política remapeados (#13). Prompt normativo p/ nISO em `audit/prompt-nISO-normas.md`. |
| 2026-08-19 | **Coleta de evidência — 17 críticos**: dossiê `audit/ENG-2026-001-evidence-collection-17-criticos.md`. 9 são N/A (sem evidência necessária); 3–4 aplicáveis já satisfazíveis por **vínculo** de evidência existente (pentest/DAST/SAST/DevSecOps órfãos); 3 exigem export do AWS (Macie/CloudTrail/WebFilter). ~~API não re-vincula evidência (UI).~~ **[CORRIGIDO em 2026-08-25 — a API re-vincula; ver abaixo]** A.8.22 N/A incorreto → reclassificar. |
| 2026-08-25 | **Aprendizado + escrita nISO APLICADA (aprovada):** descoberto que a **re-vinculação de evidência É executável pela API do consultor** (`PUT /api/v1/evidence/{id}` `{control_id}`), derrubando a premissa errada de que era "só UI". Aplicados **8 re-vínculos** (7 órfãos + 1 mis-link `ctrl-a81`→A.1.3.10) e **5 elevações `Missing→In Progress`** (A.1.2.6/A.1.3.10/A.1.4.5/A.8.8/A.8.29). Efeito: órfãos **35→28**; **Missing 10→5** (restam só A.8.11/12/15/16/23, que dependem de export AWS). Auth=`X-API-Key`; curl obrigatório (cf-1010 bloqueia urllib). Capacidades da API documentadas na seção "Acesso ao nISO". |
| 2026-08-26 | **Autorização permanente (resper@bekaa.eu, DPO/consultor):** consultor pode aplicar, em nome do DPO, os ajustes **de escopo DPO/consultor** (status/vínculo de evidência no nISO, higiene do store, documentos da alçada). **Limites mantidos:** NÃO assinar o Ato (ato do CEO), NÃO executar a 9.2 (ness/Monica), NÃO marcar `Implemented` sem evidência, NÃO fabricar evidência. |
| 2026-08-26 | **Correção A.5.15/A.5.29 (aprovada):** ambos estavam `Planned` por resíduo — subestimados (têm política + maturidade). Elevados a **`In Progress`** no nISO; `Controles_Acesso_Governanca_Fase15` vinculado a A.5.15; os 2 relatórios simulados de auditoria **desassociados** (`control_id=null`, órfãos limpos — não são revisão independente). Planned 3→1 (só A.5.35). Vínculos quebrados 2→0. `SOA.md` re-sincronizado. Placar: 23 Impl / 49 In Progress / 5 Missing / 1 Planned / 15 N/A. |
| 2026-08-26 | **Designação da auditoria interna 9.2:** parte executante = **ness Processos e Tecnologia Ltda** (CNPJ 72.027.097/0001-37), auditora-líder **Monica Yoshida Barbosa**. ness integra o mesmo grupo da Bekaa (**divulgado**); imparcialidade assegurada por **segregação de equipe** (auditora sem participação na implementação, sem vínculo com Ricardo Esper). Self-review afastado; risco residual de grupo sinalizado. Instrumento `GOV-AUD-001` criado (minuta p/ assinatura + declaração de imparcialidade + credenciais a anexar). |
| 2026-08-26 | **4 elevações a `Implemented`** (aprovadas): A.1.2.6/A.1.3.10/A.1.4.5/A.8.29 (A.8.8 mantido `In Progress`). **nISO liberou a escrita de `owner`** (solicitação de mudança de sistema): campo **`owner` "CISO" → "CIO / Responsável de Segurança"** aplicado por API em **88 controles** (0 CISO restantes; `DevOps`/`IT Manager` preservados). Placar: **27701 = 25 Impl / 6 N/A / 0 Missing**; **27001 = 23 Impl / 47 In Progress / 15 N/A / 3 Planned / 5 Missing**. Balanço de prontidão atualizado. |
