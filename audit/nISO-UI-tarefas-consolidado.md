# nISO — Tarefas de UI/Admin consolidadas (fazer de uma vez) — ENG-2026-001

> **Para quem opera o nISO (UI/admin).** Reúne, num só lugar, tudo que **não** dá para fazer pela API
> do papel consultor (re-vínculo de evidência, correção de aplicabilidade, limpeza de aprovações,
> higiene de store). Projeto: `mr9c1qugo16zic2eko`. Nenhuma ação aqui declara conformidade — apenas
> organiza evidência/estado objetivo; a verificação final é da auditoria 9.2 independente.

---

## A. Re-vincular evidência já existente ao controle certo

Evidência **já está no store** (muitas `conforme`), porém **órfã** ou vinculada ao controle errado.
Re-vincular e, em seguida, elevar o status do controle.

### A.1 — Privacidade 27701 (lote B do #14)
| Controle | id | Evidência (store) |
|---|---|---|
| A.1.2.6 — DPIA | `mszfwg85tdenmudpodd` | `Relatorio_DPIA_Privacidade_Fase9` (órfã) + `SGP-DPIA-001` |
| A.1.3.10 — Processo de atendimento | `mszfwgkcdi4s08n4z06` | `Governanca_DPO_Canal_Atendimento_Fase25` (em ctrl-a81) |
| A.1.4.5 — Minimização | `mszfwgpe8fzwl2jsoes` | `Diretrizes_Anonimizacao_Privacidade_Fase23` (órfã) |
| A.1.5.4 — Registros de transferências | `mszfwgxhgw4hgtbx51` | `Matriz_Transferencia_Internacional_Fase24` (órfã) |

### A.2 — Segurança 27001 (17 críticos / #8) — detalhe em `handoff-UI-nISO-vinculos.md`
| Controle | id | Evidência (store) |
|---|---|---|
| A.8.29 — Testes de segurança | `ctrl-a829` | `Engenharia_Seguranca_DevSecOps_Fase18`, `dast_scan_results`, `sast_pipeline_report`, `Relatorio_Pentest_...Fase32` |
| A.8.8 — Gestão de vulnerabilidades | `ctrl-a88` | `Relatorio_Pentest_Vulnerabilidades_Fase32` |
| A.8.11 — Mascaramento | `ctrl-a811` | `Diretrizes_Anonimizacao_Privacidade_Fase23` (reforçar c/ prova de masking — ver Ops) |
| A.8.16 — Monitoramento | `ctrl-a816` | `POL-THR-001`, métricas GuardDuty (reforçar c/ findings — ver Ops) |
| A.8.15 — Logs | `ctrl-a815` | política de logs + evidência CloudTrail (ver Ops) |

## B. Corrigir aplicabilidade mal-marcada (descrição de seed errada)

Estes controles têm no nISO texto do tipo "nenhum X identificado", **contradizendo** a realidade do
TWYN (100% nuvem AWS, equipe 100% remota, tratamento de biometria sensível). Marcar como **aplicável**
e ajustar a justificativa.

| Controle | Texto atual (errado) | Correção |
|---|---|---|
| A.5.23 — Serviços em nuvem | "Nenhum serviço em nuvem identificado" | **Aplicável** — toda a infra é AWS; vincular arquitetura/AWS. |
| A.6.7 — Trabalho remoto | "Nenhuma modalidade de trabalho remoto" | **Aplicável** — equipe 100% remota; política de trabalho remoto. |
| A.8.11 — Mascaramento | "Sem dados sensíveis que exijam mascaramento" | **Aplicável** — biometria (dado sensível). |
| A.8.12 — DLP | "Nenhum cenário de alto risco de vazamento" | **Aplicável** — vazamento de biometria é risco alto. |
| A.8.29 — Testes de segurança | "Sem desenvolvimento exigindo testes" | **Aplicável** — TWYN desenvolve a API. |
| A.8.22 — Segregação de redes | `Not Applicable` | **Aplicável** — VPC/Security Groups (arquitetura já existe). |

## C. Remover a designação de CISO — **decisão: TWYN não tem CISO**

**✅ FEITO por API (2026-08-24):** todas as aprovações de CISO foram **retiradas** — descoberto que
editar a `description` de um controle invalida a aprovação de CISO no nISO. Estado verificado:
`ciso_approved_by` = **0**, `ciso_approved_at` = **0**, caveats de "DESAPROVADA" = **0**. 65 controles
passaram a exibir a nota: *"A TWYN não possui cargo de CISO; responsabilidade de segurança é do CIO
(Humberto Oliveira)."*

**⬜ Resta (só UI/admin — campo `owner` não é gravável por API):**
- **`owner = "CISO"` em 88 controles** → alterar para **"CIO / Responsável de Segurança (Humberto
  Oliveira)"** (ou o rótulo que o nISO permitir), coerente com a decisão de que não há cargo de CISO.
- Se o nISO tiver um mapa de papéis por projeto, ajustar lá em vez de controle a controle.

## D. Higiene do store de evidências (#16)

- **42 evidências `pending`** — avaliar (conforme/não-conforme) — julgamento de conteúdo.
- **7 evidências órfãs** (`control_id` nulo): SOC 1/2/3, `dpaAWS`, `scc_AWS` → vincular a
  A.5.19/A.5.22/A.5.23/A.5.34 conforme o caso.
- **Padronizar `evaluation_status`** para minúsculas (`Conforme` → `conforme`).

## E. Exports do AWS (não é UI — é DevOps) — #9

Detalhe e comandos em `audit/handoff-OPS-export-AWS.md`: Macie/DLP (A.8.12), CloudTrail (A.8.15),
GuardDuty (A.8.16), filtragem web (A.8.23 — ou decisão de N/A).

## F. Fechamento

Após A–D: **elevar o status** dos controles re-vinculados e **recalcular o readiness** (27001 e
27701). Meta: derrubar os 17 críticos e levar o SGPI de 24 → 28 Implemented.
