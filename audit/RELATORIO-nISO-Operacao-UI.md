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

A adequação documental já foi feita e a maior parte dos controles está implementada.

> ✅ **Atualização 2026-08-25:** o **re-vínculo de evidência a controle** e a **elevação de status**
> foram **executados pela consultoria via API** — **não** são mais tarefa deste operador. Ver o journal
> em `audit/engagement.md`. As seções 2 e 3 abaixo ficam como **registro do que foi feito**.
>
> **Atualização 2026-08-26:** o nISO **liberou a escrita de `owner` via API** — a seção 5 (troca
> "CISO"→CIO em 88 controles) **já foi executada pela consultoria** e **não é mais tarefa de UI**.
> A "aplicabilidade" (seção 4) também não é flag separada: é o próprio `status`, e o A.8.22 já está
> `In Progress` (aplicável). **Só resta a higiene opcional do store (seção 6)**, que não bloqueia o
> Stage 1.

> Nenhuma ação aqui **declara conformidade** — apenas **anexa evidência objetiva já existente** e
> corrige metadados. O julgamento final é da **auditoria interna 9.2** (parte independente).

---

## 2. Re-vínculo de evidência de PRIVACIDADE (27701) — ✅ FEITO PELA CONSULTORIA (API)

Aplicado em 2026-08-25 (`PUT /api/v1/evidence/{id}`); status elevado `Missing→In Progress`.

| Controle 27701 | Evidência (store) | id evidência | Resultado |
|---|---|---|---|
| **A.1.2.6** — DPIA | `Relatorio_DPIA_Privacidade_Fase9` | `821518d1` | ✅ vinculada · Missing→In Progress |
| **A.1.3.10** — Atendimento a titulares | `Procedimento_Direitos_Titulares_DSAR_Fase22` + `Canal_Atendimento_Fase25` (corrigido mis-link `ctrl-a81`) | `50c8761f` / `d4460e75` | ✅ 2 evid. vinculadas · Missing→In Progress |
| **A.1.4.5** — Minimização | `Diretrizes_Anonimizacao_Privacidade_Fase23` | `84c7f9c5` | ✅ vinculada · Missing→In Progress |

## 3. Re-vínculo de evidência de SEGURANÇA (27001) — ✅ FEITO PELA CONSULTORIA (API)

| Controle 27001 | Evidência (store) | id evidência | Resultado |
|---|---|---|---|
| **A.8.29** — Testes de segurança | `Engenharia_Seguranca_DevSecOps_Fase18` | `3e5885a6` | ✅ vinculada · Missing→In Progress |
| **A.8.8** — Vulnerabilidades | `Relatorio_Pentest_Vulnerabilidades_Fase32` | `b63d7205` | ✅ vinculada · Missing→In Progress |
| **A.5.24 / A.5.9** (reforço) | `Plano_Resposta_Incidentes_Fase19` · `Inventario_Ativos_Fase7` | `2c5c2c29` / `e91be7f2` | ✅ vinculadas (já eram In Progress) |

> **A.8.11 (Mascaramento)** e os demais (**A.8.12, A.8.15, A.8.16, A.8.23**) **seguem `Missing`** —
> dependem de **export do AWS** (ver `RELATORIO-Tecnologia-Evidencias-AWS.md`). Não há órfão que os
> feche com honestidade. **Missing 10→5** após esta rodada.

## 4. Aplicabilidade — ✅ RESOLVIDO (não há flag separada)

- No nISO, "aplicável/não-aplicável" **é o próprio `status`** (`Not Applicable`), gravável por API.
  **A.8.22 — Segregação de Redes** já está `In Progress` (aplicável), com justificativa (VPC/Security
  Groups) gravada. **Nada de UI aqui.**

## 5. Campo `owner` (decisão: TWYN não tem CISO) — ✅ FEITO PELA CONSULTORIA (API)

- **`owner = "CISO"` em 88 controles → "CIO / Responsável de Segurança"** — aplicado por API em
  2026-08-26 (o nISO liberou a escrita do campo). **0 controles com "CISO"** restantes. `DevOps` (3) e
  `IT Manager` (2) preservados.
- **✅ Já feito por API (rodadas anteriores):** aprovações de CISO sem lastro (`ciso_approved_by`)
  **retiradas**.
- **Nada de UI nesta seção.**

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
