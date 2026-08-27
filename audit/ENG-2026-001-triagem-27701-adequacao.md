# Triagem de Adequação — 27701:2025 Controlador (28 controles aplicáveis) — issue #14

> **Documento de trabalho do consultor (ENG-2026-001).** Não é parecer de conformidade nem de
> certificação. Nenhuma escrita no nISO foi feita — cada elevação de status depende de **aprovação
> humana**. A verificação final (auditoria 9.2) cabe a parte independente.

**Data:** 2026-08-23 · **Fonte da verdade:** nISO (`mr9c1qugo16zic2eko`) + `soa/SGPI-SoA-27701-2025.md`.
**Base de evidência conferida:** documentos do repo + store de evidências do nISO (124 itens; os
artefatos `*_FaseNN` de privacidade constam **`conforme`**, porém a maioria **órfã** — `control_id=None` —
ou vinculada a um controle 27001, não ao controle 27701 correspondente).

## Resumo

| Categoria | Qtd | Significado | Ação |
|---|---|---|---|
| **A — Lastro documental no repo** | 21 | Documento real do ISMS cobre o controle | Propor `Missing→Implemented` no nISO citando o doc no `description` (sob aprovação) |
| **B — Evidência existe no store, mas órfã/mal-vinculada** | 4 | Artefato `conforme` no nISO, não ligado ao controle 27701 | **Re-vincular na UI do nISO** (a API do consultor não re-vincula) → depois elevar |
| **C — Decisão/documento novo** | 3 | Falta decisão de aplicabilidade ou documento | Tratar antes de elevar |

---

## Categoria A — lastro documental no repo (21) — prontos para adequação sob aprovação

| Controle | Evidência (repo) |
|---|---|
| A.1.2.2 — Finalidade | `ROPA.md` |
| A.1.2.3 — Bases legais | `ROPA.md`; Parecer Machado Meyer 116764899; `Matriz_Requisitos_Legais_Fase12` (store, conforme) |
| A.1.2.7 — Contratos com operadores | `A.5.21_Privacy` (SGP-KYV-001); `A.5.34_ICA` |
| A.1.2.8 — Controladoria conjunta | `POL-LEG-002` (`A.5.31.md`); `A.5.34_ICA` |
| A.1.2.9 — Registros de tratamento (ROPA) | `ROPA.md` |
| A.1.3.2 — Obrigações para com titulares | `A.5.34_Rights` (SGP-PRO-001) |
| A.1.3.3 — Informações a prestar | `A.5.34_Notice` (SGP-NOTICE-001) |
| A.1.3.4 — Prestação de informações | `A.5.34_Notice` |
| A.1.3.6 — Oposição ao tratamento | `A.5.34_Rights` |
| A.1.3.7 — Acesso/correção/exclusão | `A.5.34_Rights`; `Procedimento_...DSAR_Fase22` (store, conforme) |
| A.1.3.8 — Repasse a terceiros | `ROPA.md` (não há partilha de vetores — justificativa) |
| A.1.3.9 — Cópia dos DP | `A.5.34_Rights` |
| A.1.4.2 — Limitação da coleta | `ROPA.md` (só selfie) |
| A.1.4.3 — Limitação do tratamento | `ROPA.md` |
| A.1.4.6 — Desidentificação/eliminação | `POL-GOV-001` (§4); `ROPA.md` |
| A.1.4.7 — Arquivos temporários | `ROPA.md` (expurgo RAM 0s) |
| A.1.4.8 — Retenção | `POL-GOV-001` (§3, tabela de temporalidade) |
| A.1.4.9 — Descarte seguro | `POL-GOV-001` (§4) |
| A.1.4.10 — Transmissão | `A.8.24` (cripto); TLS 1.3 (`ROPA.md`) |
| A.1.5.3 — Países de destino | `ROPA.md` (AWS `sa-east-1`/Brasil — sem transferência internacional; _Correção NC-04: era us-east-1_) |
| A.1.5.5 — Divulgação a terceiros | `ROPA.md` (resposta booleana; sem partilha) |

## Categoria B — evidência existe no store (conforme) mas precisa de re-vínculo na UI (4)

| Controle | Evidência no store nISO | Situação |
|---|---|---|
| A.1.2.6 — DPIA | `Relatorio_DPIA_Privacidade_Fase9` (órfã) + `SGP-DPIA-001` (`approved`, em ctrl-a534) | Re-vincular ao A.1.2.6 |
| A.1.3.10 — Processo de atendimento | `Governanca_DPO_Canal_Atendimento_Fase25` (`conforme`, em ctrl-a81) | Re-vincular ao A.1.3.10 |
| A.1.4.5 — Minimização | `Diretrizes_Anonimizacao_Privacidade_Fase23` (órfã) | Re-vincular ao A.1.4.5 |
| A.1.5.4 — Registros de transferências | `Matriz_Transferencia_Internacional_Fase24` (órfã) | Re-vincular ao A.1.5.4 (após decisão C de A.1.5.2) |

> Re-vínculo depende da **UI/admin do nISO** — a API do papel consultor não re-liga evidência a
> controle (mesma limitação da issue #8). Consolida-se no handoff de UI.

## Categoria C — decisão/documento novo antes de elevar (3)

| Controle | Questão | Encaminhamento |
|---|---|---|
| **A.1.3.11 — Decisões automatizadas** | O match facial devolve booleano+score que **subsidia decisão** do parceiro B2B. Há decisão automatizada com efeito ao titular? | Decisão de governança + registro: TWYN fornece o resultado; a decisão sobre o titular é do controlador-parceiro. Documentar o enquadramento e informação ao titular (LGPD Art. 20). |
| **A.1.4.4 — Exatidão/qualidade dos DP** | Sem evidência candidata. | Documentar mecanismo de exatidão (liveness/qualidade de captura, score de similaridade, tratamento de falso-positivo/negativo). Documento novo curto. |
| **A.1.5.2 — Base de transferência internacional** | Matriz existe, mas cita **SCC** (mecanismo do GDPR). Sob LGPD, transferência internacional se rege pelos Arts. 33–36 (cláusulas-padrão da ANPD/adequação), **não** SCC do GDPR. | **Corrigir o mecanismo** para a base da LGPD/ANPD antes de elevar. |

---

## Recomendação de sequência (cada escrita sob aprovação)

1. **Aprovar o lote A (21):** elevar `Missing→Implemented` no nISO citando o documento de lastro no
   campo `description` (rastreável), sem tocar em campos de aprovação (imutáveis).
2. **Lote B (4):** re-vincular as 4 evidências na UI do nISO → depois elevar.
3. **Lote C (3):** A.1.5.2 corrigir mecanismo (LGPD, não SCC); A.1.4.4 e A.1.3.11 gerar documento/decisão.
4. **Recalcular readiness** 27701 e re-baseline.

> Observação de maturidade: "Implemented" aqui reflete **existência de controle documentado com
> lastro**; a maturidade operacional (CMM) e a verificação de operação efetiva ficam para a
> auditoria interna independente (9.2).
