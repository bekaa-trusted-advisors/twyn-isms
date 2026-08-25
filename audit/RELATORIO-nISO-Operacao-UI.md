# Ações no nISO (UI/Admin) — Vínculo de Evidências e Ajustes · TWYN Face ID Platform

| | |
|---|---|
| **Para** | Quem opera o nISO (Encarregado/DPO ou consultor com acesso à UI/admin) |
| **De** | Consultoria de Adequação ISO 27001/27701 (ENG-2026-001) |
| **Data** | 2026-08-25 |
| **Projeto nISO** | `mr9c1qugo16zic2eko` |
| **Assunto** | Ações que **só a tela/admin do nISO permite** (a API do papel consultor não executa) |

---

## 1. Contexto

A adequação documental já foi feita e a maior parte dos controles está implementada. As ações abaixo
**não** podem ser feitas pela API (re-vínculo de evidência a controle, alteração do campo `owner`,
higiene do store) — precisam da **UI/admin**. Ao final, os controles saem de `Missing` e o readiness é
recalculado.

> Nenhuma ação aqui **declara conformidade** — apenas **anexa evidência objetiva já existente** e
> corrige metadados. O julgamento final é da **auditoria interna 9.2** (parte independente).

---

## 2. Re-vincular evidência de PRIVACIDADE (27701 — 3 Missing)

A evidência já está no store, marcada `conforme`, porém **órfã** (`control_id` nulo) ou no controle
errado. Re-vincular ao controle 27701 e depois elevar o status.

| Controle 27701 | Evidência (store) | id evidência | Situação |
|---|---|---|---|
| **A.1.2.6** — DPIA | `Relatorio_DPIA_Privacidade_Fase9` + `SGP-DPIA-001` | `821518d1` | órfã / SGP em ctrl-a534 |
| **A.1.3.10** — Canal de atendimento | `Governanca_DPO_Canal_Atendimento_Fase25` | `d4460e75` | está em `ctrl-a81` |
| **A.1.4.5** — Minimização | `Diretrizes_Anonimizacao_Privacidade_Fase23` | `84c7f9c5` | órfã |

## 3. Re-vincular evidência de SEGURANÇA (27001 — parte dos 7 Missing / #8)

| Controle 27001 | Evidência (store) | id evidência |
|---|---|---|
| **A.8.29** — Testes de segurança | `Engenharia_Seguranca_DevSecOps_Fase18`, `dast_scan_results`, `sast_pipeline_report`, `Relatorio_Pentest_...Fase32` | `3e5885a6` / `b63d7205` |
| **A.8.8** — Vulnerabilidades | `Relatorio_Pentest_Vulnerabilidades_Fase32` | `b63d7205` |
| **A.8.11** — Mascaramento | `Diretrizes_Anonimizacao_Privacidade_Fase23` (reforçar com prova de masking — ver relatório de TI) | `84c7f9c5` |

> Os demais (A.8.12, A.8.15, A.8.16, A.8.23) dependem de **export do AWS** (ver
> `RELATORIO-Tecnologia-Evidencias-AWS.md`) antes de vincular.

## 4. Corrigir aplicabilidade

- **A.8.22 — Segregação de Redes** está `Not Applicable` — **incorreto** para plataforma cloud. Marcar
  **Aplicável** e vincular a arquitetura de VPC/Security Groups.

## 5. Ajustar o campo `owner` (decisão: TWYN não tem CISO)

- **`owner = "CISO"` em 88 controles** → alterar para **"CIO / Responsável de Segurança (Humberto
  Oliveira)"** (ou o rótulo que o nISO permitir). *(A API não grava `owner`.)*
- **✅ Já feito por API:** as aprovações de CISO sem lastro (`ciso_approved_by`) foram **retiradas** —
  não há ação de UI aqui.

## 6. Higiene do store de evidências (#16)

- **~42 evidências `pending`** — avaliar (conforme / não-conforme): julgamento de conteúdo.
- **~35 evidências órfãs** (`control_id` nulo) — vincular ao controle certo. Ex.:
  - `SOC 1/2/3` e `dpaAWS.pdf` → **A.5.19/A.5.22** (fornecedor AWS).
  - `scc_AWS_Service_Terms` → **A.5.19** (termos do fornecedor). *Obs.: não usar como "transferência
    internacional" — os dados estão em `sa-east-1`/Brasil.*
- **Padronizar `evaluation_status`** para minúsculas (`Conforme` → `conforme`).

## 7. Anexar evidências novas (ingeridas nesta rodada)

| Evidência (PDF) | Vincular ao controle |
|---|---|
| **Contrato de DPO-as-a-Service** (TWYN, assinado) | Governança/DPO (A.5.34 / registro GOV-DPO) |
| **EVICERT** (treinamento SI/LGPD, 100%) | **A.6.3** (já elevado; anexar o PDF) |
| **EVITERMOS / EVIPRO04** (termos de sigilo) | **A.6.6** (já elevado; anexar o PDF) |
| **Cartão CNPJ** oficial da Bekaa | evidência do arranjo de DPO |

## 8. Fechamento

Após as ações 2–4 e 7: **elevar o status** dos controles re-vinculados e **recalcular o readiness**
(27001 e 27701). Meta: 27701 24 → 27+ Implemented e derrubar os críticos do 27001.
