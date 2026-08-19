# Análise Integrada SGSI + SGPI — Gaps, Não Conformidades e Plano de Ação

| Campo | Valor |
|---|---|
| **Engajamento / Contrato** | ENG-2026-001 / C-2026-08-18-01 |
| **Cliente** | TWYN — Face ID Platform (biometria facial, AWS us-east-1, LGPD) |
| **Escopo** | ISO/IEC 27001:2022 (SGSI) + ISO/IEC 27701:2025 (SGPI), papel **Controlador** |
| **Fontes cruzadas** | nISO (fonte da verdade: 124 controles, readiness, evidências, ROPA, fases, certificação) × repo `twyn-isms` (SOA/RISKS/ROPA/POLICIES/EVIDENCE) |
| **Data** | 2026-08-19 |
| **Modo** | CONSULTOR — análise de adequação |

> **Natureza.** Análise de **consultor sênior** para dirigir a adequação. **Não é** a auditoria
> interna (9.2, exige sessão independente) **nem** parecer de certificação. **Nenhuma evidência foi
> criada**; nenhum status foi presumido conforme. Achados ancorados na fonte da verdade (nISO) e nos
> artefatos do repo.

---

## 1. Sumário executivo — veredito de prontidão

**O ambiente NÃO está apto a certificação**, ao contrário do que o repositório declarava
(`IPC 100% / Audit Ready`). A fonte da verdade (nISO) contradiz essa declaração em **todas** as camadas:

- **Controles:** dos 124 (93 do 27001:2022 + 31 do 27701:2025), **0 estão `Implemented`**.
  27001 → 6 `In Progress`, 69 `Missing`, 2 `Planned`, 16 `N/A`. 27701 → 28 `Missing`, 3 `N/A`.
- **Diagnóstico do próprio nISO (readiness):** **66 achados — 17 críticos + 49 médios**.
- **Integridade:** **48 controles** figuram `Missing` mas carregam **maturidade 3–5**; **17 controles**
  estão **assinados (CISO/CEO) sem qualquer evidência anexada**.
- **Jornada de gestão:** respondida apenas até a **fase 1** (mandato + apetite de risco). As "41 fases
  executadas" alegadas no repo **não existem** na fonte da verdade.
- **Certificação (nISO):** estágio **`Gap Assessment`**, Stage 1 e Stage 2 **`Pending`** — os "pareceres
  de Estágio 1/2" do repo **não têm lastro** no nISO.

**Conclusão:** o SGSI/SGPI está em fase inicial de adequação real. A prioridade imediata (P0) é
**restaurar a integridade dos dados** (status × maturidade × assinatura × evidência) antes de qualquer
avaliação; só então a implementação efetiva dos controles.

---

## 2. Panorama quantitativo (fonte da verdade — nISO)

### 2.1 Controles por norma × status
| Norma | Implemented | In Progress | Planned | Missing | Not Applicable | Total |
|---|---:|---:|---:|---:|---:|---:|
| ISO 27001:2022 | 0 | 6 | 2 | 69 | 16 | 93 |
| ISO 27701:2025 | 0 | 0 | 0 | 28 | 3 | 31 |
| **Total** | **0** | **6** | **2** | **97** | **19** | **124** |

### 2.2 Readiness (auto-diagnóstico nISO) — 66 achados
| Severidade | Categoria | Qtde |
|---|---|---:|
| Crítico | `doc_inconsistente` — "assinatura sem lastro" (assinado sem evidência) | 17 |
| Médio | `doc_inconsistente` — status × maturidade × evidência incoerentes | 48 |
| Médio | `doc_faltante` | 1 |

### 2.3 Evidências — cobertura e qualidade
| Métrica | Valor |
|---|---|
| Itens de evidência (nISO) | 124 |
| Controles com ≥1 evidência | **60 / 124** (⇒ **64 sem evidência**) |
| `evaluation_status` | pending **42** · conforme **44** (casing misto `conforme`/`Conforme`) · approved **38** |
| Evidências órfãs (control_id inexistente) | 7 itens (3 ids) |

### 2.4 Jornada e ROPA
| Item | Estado |
|---|---|
| `phase-answers` | **8 respostas** (fases 0–1 apenas): mandato assinado (CEO), papéis definidos, apetite `Baixo`, objetivos aprovados |
| ROPA | **1 registro** (fluxo biométrico único; base legal Art. 11 II g) |
| Certificação | estágio `Gap Assessment`; Stage 1 `Pending`; Stage 2 `Pending` |

---

## 3. Não Conformidades e Gaps (classificados)

### NC MAIORES (bloqueiam certificação)

**NC-01 — Incoerência sistêmica status × maturidade (integridade de dados).**
48 controles `Missing` com maturidade 3–5 (24@3, 20@4, 4@5). Um controle inexistente não tem maturidade
alta. *Cláusula:* 7.5 (informação documentada), 9.1. *Evidência:* readiness `doc_inconsistente` (48).

**NC-02 — Assinatura sem lastro (17 controles críticos).**
Controles aprovados/assinados por CISO/CEO **sem evidência anexada**: A.7.1–7.6, A.7.8, A.7.11, A.7.12,
A.8.8, A.8.11, A.8.12, A.8.15, A.8.16, A.8.22, A.8.23, A.8.29. Aprovação sem evidência mina a
confiabilidade de todo o SoA. *Cláusula:* 7.5, 9.2/5.2 (aprovação responsável). *Evidência:* readiness 17 críticos.

**NC-03 — Declaração de conformidade sem base ("IPC 100% / Audit Ready").**
Repo declara 49 `Implemented` / 100%; fonte da verdade mostra **0 `Implemented`** e 69 `Missing` (27001).
*Cláusula:* 5.2, 9.3 (representações à direção), 10.2. *Ação:* já iniciada (PR #2/#3: status → `In Progress`).

**NC-04 — SGPI (27701) sem implementação.**
Até 2026-08-19 não havia **nenhum** controle 27701 no nISO; o control-set 2025 (31) foi semeado neste
engajamento e está **0 implementado**. *Cláusula:* 27701 cláusulas 5–8. *Ação:* adequação dos 28 aplicáveis.

**NC-05 — Evidências: 42 pendentes, 64 controles sem evidência, 7 órfãs, e (no repo) trilha não fidedigna.**
42 evidências `pending` (não avaliadas); 64/124 controles sem evidência; 7 evidências órfãs. No repo, as
~47 evidências têm **data única (2026-07-27)** e os artefatos de auditoria são **stubs** (Estágio 1 = 17
linhas; Estágio 2 = 19). *Cláusula:* 7.5, 9.2, 8.1. *Risco:* não resistem a certificador.

**NC-06 — Jornada de gestão parada na fase 1 / cláusulas 4–10 não evidenciadas.**
Só fases 0–1 respondidas. Contexto (4), liderança (5, além do mandato), planejamento (6), apoio (7),
operação (8), avaliação (9) e melhoria (10) não têm artefatos de gestão rastreáveis na fonte da verdade.
*Cláusula:* 4–10 integral.

**NC-07 — Evidência de auditoria interna e Stage 1/2 sem lastro.**
Repo alega pareceres de Estágio 1/2; nISO em `Gap Assessment`, Stage 1/2 `Pending`. Auditoria interna
(9.2) declarada mas sem trilha independente verificável. *Cláusula:* 9.2, 9.3, 10.

**NC-08 — Independência do DPO comprometida.**
Acúmulo **DPO + CISO + Consultor** numa só pessoa (Ricardo Esper); "CISO" atribuído a 3 nomes distintos.
*Cláusula:* 5.3 (segregação), 27701 (independência do DPO), 9.2 (independência da auditoria).

### NC MENORES / OBSERVAÇÕES

- **OBS-01 — ROPA de fluxo único:** só 1 atividade de tratamento registrada; prováveis fluxos ausentes
  (colaboradores/RH, logs, suporte). *Cláusula:* 27701 / LGPD Art. 37.
- **OBS-02 — Registro de riscos uniforme:** 12 riscos todos `Low`/`Mitigated`, sem inerente×residual, sem
  score numérico apesar da metodologia 1–5; 3 já reabertos (apoiavam-se em controles `Missing`).
- **OBS-03 — Vocabulário/casing inconsistente:** status `Approved` (repo) fora do padrão; evidências
  `conforme`/`Conforme`. Padronizar.
- **OBS-04 — Transferência internacional:** mecanismo citado como "SCC" (padrão UE/GDPR); rever base sob
  LGPD/ANPD para o fluxo us-east-1.
- **OBS-05 — Caminhos locais Windows** (`file:///c:/Users/...`) embutidos em README/SOA/POLICIES/EVIDENCE.
- **OBS-06 — Aplicabilidade N/A questionável:** A.7.10/7.13/7.14 marcados N/A com texto "aplica-se a todas
  as organizações". Rever.

---

## 4. Cruzamento repo × fonte da verdade (nISO)

| Dimensão | Repo `twyn-isms` | nISO (verdade) | Veredito |
|---|---|---|---|
| Status geral | `Audit Ready` / IPC 100% | `In Progress` (corrigido); 0 Implemented | **Divergência crítica** |
| Controles 27001 Implemented | 49 | 0 | **Divergência crítica** |
| Controles 27701 | "catalogados" (só rótulo) | 31 semeados, 0 implementados | Repo desatualizado |
| Evidências | ~47 (data única, stubs) | 124 (42 pending, 7 órfãs) | Ambos frágeis; desalinhados |
| Fases | "41 executadas" | 8 respostas (fases 0–1) | **Alegação sem lastro** |
| Estágio de certificação | Estágio 1/2 "emitidos" | `Gap Assessment`, Pending | **Alegação sem lastro** |
| Versão SGPI | 27701:2019 | 27701:2025 (migrado) | Corrigido neste engajamento |

---

## 5. Plano de Ação detalhado

Prioridades: **P0** = integridade/veracidade (pré-condição de tudo); **P1** = implementação e evidência;
**P2** = maturidade e otimização. Responsáveis são **sugestões** a confirmar com a governança.

### P0 — Restaurar integridade e veracidade (antes de qualquer avaliação)

| # | Ação | NC | Responsável | Critério de aceite | Dependência |
|---|---|---|---|---|---|
| P0.1 | Reconciliar **status × maturidade** dos 48 controles incoerentes contra evidência real; rebaixar/abrir os sem lastro | NC-01 | Consultor + CISO | 0 controles `Missing` com maturidade >0 sem justificativa; readiness `doc_inconsistente` → 0 | nISO write |
| P0.2 | Remover/renovar **assinaturas sem lastro** (17): retirar aprovação até haver evidência, ou anexar evidência | NC-02 | CISO/CEO | 0 achados críticos "assinatura sem lastro" | P0.1 |
| P0.3 | Propagar a correção "**não Audit Ready**" a todos os artefatos (repo já em PR #2/#3; nISO já `In Progress`) | NC-03 | Consultor | Repo e nISO coerentes; sem "100%" | — |
| P0.4 | Sanear evidências: avaliar as **42 pending**, remover **7 órfãs**, padronizar casing; substituir stubs por evidência real datada | NC-05 | DPO + CISO | 0 pending sem decisão; 0 órfãs | — |
| P0.5 | Formalizar **independência do DPO** e organograma com segregação (5.3) | NC-08 | CEO | DPO independente do CISO/consultor documentado | — |

### P1 — Implementar controles e produzir evidência

| # | Ação | NC | Responsável | Critério de aceite | Dependência |
|---|---|---|---|---|---|
| P1.1 | Fechar os **6 `In Progress` + 2 `Planned`** do 27001 (implementar + evidência + aprovação) | NC-01/05 | CISO | 8 controles `Implemented` com evidência | P0 |
| P1.2 | Tratar os **69 `Missing`** do 27001 por onda de risco (priorizar os ligados a riscos reabertos: A.5.17, A.8.9, A.8.12) | NC-01 | CISO | Plano de implementação por controle; risco residual reavaliado | P0.1 |
| P1.3 | **SGPI 27701:2025** — adequar os **28 aplicáveis** (mapear evidência candidata → implementar → status), começando por A.1.2.9 (ROPA), A.1.3.7/10 (direitos), A.1.4.6/8 (retenção/descarte), A.1.5.2 (transferência) | NC-04 | DPO | 28 controles com status/evidência; SoA de privacidade completa | P0.1 |
| P1.4 | **ROPA** — inventariar todos os fluxos de tratamento (não só o biométrico) | OBS-01 | DPO | ROPA cobre RH, logs, suporte, etc. | — |
| P1.5 | **Riscos** — reintroduzir inerente×residual e scores; reavaliar os 12 + os 3 reabertos | OBS-02 | CISO | Matriz com score e residual; sem "Mitigated" sem controle | P1.2 |

### P2 — Sistema de gestão (cláusulas 4–10) e maturidade

| # | Ação | NC | Responsável | Critério de aceite | Dependência |
|---|---|---|---|---|---|
| P2.1 | Completar a **jornada de fases 2025** (além da fase 1) e documentar cláusulas 4–10 | NC-06 | Consultor + CISO | Fases respondidas; artefatos de gestão 4–10 presentes | esquema 2025 |
| P2.2 | Rever **transferência internacional** (base LGPD/ANPD, não SCC) | OBS-04 | DPO/Jurídico | Mecanismo de transferência válido documentado | P1.3 |
| P2.3 | **Auditoria interna real (9.2)** por sessão/agente **independente** — não pelo consultor | NC-07 | Auditor independente | Relatório 9.2 independente; achados tratados (10.2) | P0, P1 |
| P2.4 | Higiene documental (caminhos relativos, contagens, vocabulário) | OBS-03/05 | Consultor | Docs sem caminhos locais; contagens conferem | — |
| P2.5 | Após P0–P2: recomputar **readiness** e reavaliar prontidão para Stage 1 | todas | Consultor | Readiness sem críticos; IPC real calculado | tudo acima |

---

## 6. Sequência recomendada e marcos

1. **Marco A (integridade):** concluir P0 → readiness sem achados críticos; dados coerentes.
2. **Marco B (implementação núcleo):** P1.1–P1.3 → controles ativos com evidência; SGPI adequado.
3. **Marco C (gestão):** P2.1–P2.2 → cláusulas 4–10 e privacidade completas.
4. **Marco D (verificação independente):** P2.3 → auditoria interna 9.2 **independente**.
5. **Marco E (prontidão):** P2.5 → decisão informada de ida a Stage 1.

> **Independência (lei Aegis):** os itens de **implementação/adequação** são do consultor. A **auditoria
> interna 9.2** (Marco D) e o parecer de prontidão final **exigem sessão/agente independente** — não quem
> adequou. Toda escrita no nISO segue **proposta → aprovação humana → aplicação**.
