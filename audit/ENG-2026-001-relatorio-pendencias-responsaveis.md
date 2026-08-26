# Relatório de Pendências para o Stage 1 — TWYN Face ID Platform

| | |
|---|---|
| **Engajamento** | ENG-2026-001 (adequação ISO/IEC 27001:2022 + 27701:2025) |
| **Data** | 2026-08-26 |
| **Fonte da verdade** | nISO (projeto `mr9c1qugo16zic2eko`) — `SOA.md` do repo já reconciliado (0 divergências) |
| **Natureza** | Relatório de **prontidão/pendências** — **não** é parecer de conformidade nem de certificação |

---

## 1. Onde estamos (placar atual)

| Norma | Implemented | In Progress | Missing | Planned | N/A |
|---|---|---|---|---|---|
| **ISO 27001 (93)** | 23 | 47 | **5** | 3 | 15 |
| **ISO 27701 (31)** | 25 | — | **0** | — | 6 |

> Privacidade (27701) está **sem Missing**. A segurança (27001) tem **5 Missing técnicos** e **47
> In Progress** (implementados, mas com a **evidência de operação** ainda a verificar).

---

## 2. Pendências, responsável e o que fecha cada uma

### 🔴 Bloco A — Controles técnicos sem evidência (dependem do AWS)
**Responsável: Tecnologia / DevOps — Marcelo Negrão Filho · Nizar Elouaer (CTO)**
*(apoio: Humberto Oliveira — CIO / Resp. Segurança)*

| Controle | O que falta | Evidência a extrair (AWS `sa-east-1`) |
|---|---|---|
| **A.8.12** — DLP | prova de prevenção de vazamento | AWS Macie (findings 90d), S3 Block Public Access |
| **A.8.15** — Logs | prova de trilha de auditoria | CloudTrail multi-região + LogValidation; retenção |
| **A.8.16** — Monitoramento | prova de monitoramento contínuo | GuardDuty + AWS Config + Security Hub |
| **A.8.11** — Mascaramento | prova de masking em não-produção | consulta/print de anonimização fora de produção |
| **A.8.23** — Filtragem Web | prova **ou** justificativa de N/A | MDM/endpoint **ou** declarar N/A (equipe remota) |
| **A.8.8** — Vulnerabilidades *(In Progress)* | reforço do lastro | AWS Inspector/ECR scan + SLA de remediação |

> Procedimento de entrega já detalhado em `audit/RELATORIO-Tecnologia-Evidencias-AWS.md`. Os relatórios
> de gestão da CAIXA (REL-18.18/18.19) podem **acompanhar** os exports como corroboração.

### 🟠 Bloco B — 47 controles `In Progress` (evidência de operação a verificar)
**Responsável: Auditoria interna 9.2 — ness / Monica Yoshida Barbosa**
*(dona do programa: direção da TWYN)*

- São controles **implementados e documentados**, mas cuja **operação efetiva** precisa ser
  **verificada** para subir a `Implemented`. Quem faz essa verificação é a **auditoria 9.2** — não a
  consultoria (vedação à autorrevisão). É o passo que converte "In Progress com lastro" em "Implemented".

### 🟡 Bloco C — 3 controles `Planned`
**Responsável: conforme o controle**

| Controle | Responsável | Observação |
|---|---|---|
| **A.5.35** — Análise Crítica Independente | ness / Monica (9.2) | executado **pela** auditoria 9.2 |
| **A.5.15** — Controle de Acesso | Humberto (CIO) / DevOps | revisar status (parece subestimado) — validar evidência |
| **A.5.29** — Continuidade em Interrupção | Humberto (CIO) | revisar status — BCP existe (ver A.5.30) |

### 🟢 Bloco D — Governança e assinaturas
**Responsável: Alta direção**

| Item | Responsável | Documento |
|---|---|---|
| Assinar o **Ato de Nomeação do DPO** | **Kacio Giuliano Lopes** (CEO) | `GOV-DPO-001` |
| Anexar **contrato de DPO assinado** + **Cartão CNPJ** da Bekaa | DPO (Bekaa) / Jurídico | `GOV-DPO-002` |
| Homologar (assinar) a **SoA** | Resp. Segurança (Humberto) + CEO | `SOA.md` |
| **Análise Crítica pela Direção** (cl. 9.3) | CEO + direção | ata a produzir após a 9.2 |

### 🔵 Bloco E — Auditoria interna 9.2 (o gargalo formal)
**Responsável: ness / Monica Yoshida Barbosa** *(designação `GOV-AUD-001`)*

| Passo | Responsável |
|---|---|
| Assinar a **Declaração de Imparcialidade** + anexar credenciais | ness / Monica |
| Aprovar a designação | Direção TWYN |
| **Executar** a auditoria (27001+27701) e emitir relatório | ness / Monica |
| Tratar **não conformidades** (cl. 10.2) | Direção + responsáveis dos controles |

### ⚪ Bloco F — Higiene de evidências no nISO (não bloqueia o Stage 1)
**Responsável: DPO / operador do nISO** *(apoio da consultoria)*

- **50 evidências `pending`** — avaliar conforme/não-conforme (julgamento de conteúdo).
- **2 vínculos "quebrados"** (relatórios simulados de auditoria) — mantidos órfãos **de propósito**
  (são simulação da consultoria, não revisão independente); podem ser desassociados formalmente.
- **28 órfãs** legítimas (artefatos de sistema de gestão) — sem controle do Anexo A; por design.

---

## 3. Matriz de responsáveis (resumo)

| Responsável | Papel | O que está na mão dele |
|---|---|---|
| **Marcelo Negrão Filho** | Infra / DevOps | Bloco A — exports do AWS |
| **Nizar Elouaer** | CTO / Diretor Técnico | Bloco A — apoio técnico |
| **Humberto Oliveira** | CIO / Resp. Segurança | Bloco A (apoio), C, D (homologar SoA) |
| **Kacio Giuliano Lopes** | CEO | Bloco D — assinaturas de alta direção; 9.3 |
| **Enes F. Degasperi** | Diretor Financeiro / Procurador | Bloco D — contrato/cartão CNPJ (jurídico) |
| **DPO — Bekaa (Ricardo Esper, resp. técnico)** | Encarregado | Bloco D/F — anexos e higiene |
| **ness / Monica Yoshida Barbosa** | Auditoria interna 9.2 | Bloco B, C (A.5.35), E — a auditoria |
| **Consultoria (Aegis/Bekaa)** | Apoio | Vincular evidências no nISO; **não** audita |

---

## 4. Caminho crítico até o Stage 1

1. **Bloco A** (TI) → derruba os 5 Missing e reforça A.8.8.
2. **Bloco D** (direção) → instrumentos de governança em vigor.
3. **Bloco E** (ness/Monica) → executa a 9.2 → converte os 47 `In Progress` em `Implemented`
   verificado e emite o **parecer de prontidão**.
4. Só então: **agendar o organismo certificador** (Stage 1 documental → Stage 2 em campo).

> O **Bloco E é o gargalo formal**: sem a auditoria 9.2 independente, não há parecer de prontidão — e
> ela não pode ser feita pela consultoria que implementou.
