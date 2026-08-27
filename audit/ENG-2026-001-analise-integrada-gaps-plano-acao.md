# Análise Integrada SGSI + SGPI — Gaps, Não Conformidades e Plano de Ação

| Campo | Valor |
|---|---|
| **Engajamento / Contrato** | ENG-2026-001 / C-2026-08-18-01 |
| **Cliente** | TWYN — Face ID Platform (biometria facial, AWS `sa-east-1` — São Paulo/Brasil, LGPD) |
| **Escopo** | ISO/IEC 27001:2022 (SGSI) + ISO/IEC 27701:2025 (SGPI), papel **Controlador** (LGPD Art. 11 II 'g') |
| **Fontes cruzadas** | nISO (fonte da verdade: 124 controles, evidências, ROPA, fases, certificação) × repo `twyn-isms` (SOA/RISKS/ROPA/POLICIES/EVIDENCE) × **evidência de ambiente AWS** entregue pelo dev em 2026-08-27 (documento **RESTRITO**, fora deste repo) |
| **Data (regeração)** | 2026-08-27 |
| **Substitui** | versão 2026-08-19 (placar "0 Implemented / 69 Missing", já superada) |
| **Modo** | CONSULTOR — análise de adequação |

> **Natureza.** Análise de **consultor sênior** para dirigir a adequação. **Não é** a auditoria
> interna (9.2, exige sessão independente) **nem** parecer de certificação. **Nenhuma evidência foi
> criada**; nenhum status foi presumido conforme. Achados ancorados na fonte da verdade (nISO), nos
> artefatos do repo e na evidência de ambiente entregue pela TI.

> 🔒 **Confidencialidade.** A evidência de ambiente AWS (coleta de 27/08/2026) é **RESTRITA** e **não é
> versionada neste repositório público**. Este documento cita seus achados **em nível de controle**, sem
> reproduzir identificadores de conta, IPs, portas, regras de firewall específicas ou políticas de acesso —
> esses detalhes ficam no documento restrito e no nISO.

---

## 1. Sumário executivo — veredito de prontidão

**O ambiente evoluiu de "declaração sem lastro" (agosto/18) para adequação real em andamento**, porém
**ainda NÃO está apto a certificação**. A integridade dos dados foi restaurada (o placar do nISO agora
reflete implementação real, não mais "100% / Audit Ready" fictício), e a evidência de ambiente entregue
pela TI **confirmou operação de vários controles técnicos** — mas **expôs gaps técnicos reais** que
precisam de tratamento antes do Stage 1.

- **Controles (nISO, fonte da verdade):** dos 124 (93 do 27001:2022 + 31 do 27701:2025):
  - **27001 → 22 `Implemented` · 52 `In Progress` · 1 `Planned` · 2 `Missing` · 16 `N/A`.**
  - **27701 → 25 `Implemented` · 6 `N/A`.**
- **Marco de integridade (P0) concluído:** o placar agora tem lastro; a declaração "IPC 100% / Audit
  Ready" foi retirada; status e maturidade reconciliados; SoA do repo reconciliado ao nISO (0 divergências).
- **Evidência de ambiente AWS (27/08/2026):** validou A.8.8 (varredura de vulnerabilidades ativa) e
  A.8.15 (logging) como **operantes**; justificou A.8.23 como **N/A**; mas revelou que **A.8.12 (DLP/
  exposição de rede)** e **A.8.29 (teste de segurança no SDLC)** **não operam como declarado** — e A.8.16
  (monitoramento/alarmes) está **parcial**.
- **Correção material de status:** **A.8.29 foi rebaixado `Implemented → In Progress`** (2026-08-27) —
  o ambiente não possui SAST/DAST operante; a declaração anterior de "Implementado" não se sustentava.

**Conclusão:** o SGSI/SGPI saiu da fase de "dados incoerentes" e está em **implementação avançada**, mas
com um **núcleo técnico crítico em aberto** — exposição de rede/prevenção de vazamento (A.8.12),
monitoramento reativo (A.8.16), teste de segurança no desenvolvimento (A.8.29) e mascaramento de dados
(A.8.11). Há ainda **exposições ao vivo de severidade alta** no ambiente (seção 3.1) que demandam
tratamento **imediato**, independentemente do cronograma de certificação.

---

## 2. Panorama quantitativo (fonte da verdade — nISO)

### 2.1 Controles por norma × status — **atual (2026-08-27)**
| Norma | Implemented | In Progress | Planned | Missing | Not Applicable | Total |
|---|---:|---:|---:|---:|---:|---:|
| ISO 27001:2022 | 22 | 52 | 1 | 2 | 16 | 93 |
| ISO 27701:2025 | 25 | 0 | 0 | 0 | 6 | 31 |
| **Total** | **47** | **52** | **1** | **2** | **22** | **124** |

> Evolução desde 2026-08-19 (era 0 Implemented / 97 Missing / 6 In Progress): a integridade foi restaurada
> e a implementação real avançou. Os **2 `Missing`** remanescentes do 27001 são **A.8.11** (Mascaramento de
> Dados) e **A.8.12** (Prevenção de Vazamento de Dados / DLP). O único `Planned` é **A.5.35** (Análise
> Crítica Independente da SI).

### 2.2 Aplicáveis vs. implementados
| Norma | Aplicáveis (excl. N/A) | Implementados | % implementado (aplicáveis) |
|---|---:|---:|---:|
| ISO 27001:2022 | 77 | 22 | ≈ 29% |
| ISO 27701:2025 | 25 | 25 | 100% |
| **Consolidado** | **102** | **47** | **≈ 46%** |

> O SGPI (27701) está formalmente completo em status; o SGSI (27001) tem a maior parte dos controles
> aplicáveis ainda `In Progress` — implementados mas pendentes de evidência objetiva e/ou aprovação, ou
> em implementação efetiva. O número que importa para o Stage 2 não é o status declarado e sim a
> **evidência de operação** por trás de cada `Implemented`/`In Progress`.

---

## 3. Não Conformidades e Gaps (classificados)

### 3.1 🔴 Exposições ao vivo — tratamento IMEDIATO (independem do cronograma de certificação)

A evidência de ambiente (RESTRITA) revelou condições que representam **risco operacional atual** ao
tratamento de dados biométricos. Estas **não são apenas gaps documentais** — são exposições reais em
produção que devem ser corrigidas com prioridade máxima. **Detalhes técnicos (contas, IPs, portas,
regras) estão no documento restrito e no nISO; não são reproduzidos aqui.**

| # | Condição (nível de controle) | Controle | Risco |
|---|---|---|---|
| EXP-01 | Acesso administrativo remoto exposto à internet pública em regras de firewall abrangentes | A.8.20 / A.8.22 / A.8.12 | Superfície de ataque direta a hosts de gestão |
| EXP-02 | Acesso raiz (conta-mestre da nuvem) sem segundo fator | A.5.15 / A.8.5 | Comprometimento total do ambiente se a credencial vazar |
| EXP-03 | Política de acesso a recurso de armazenamento excessivamente permissiva | A.8.3 / A.5.15 | Acesso amplo indevido a dados |
| EXP-04 | Ferramenta de descoberta/classificação de dados sensíveis desabilitada | A.8.12 / A.5.12 | Dados pessoais/biométricos sem inventário nem alerta de exposição |
| EXP-05 | Ausência de bloqueio de acesso público no nível da conta de armazenamento | A.8.3 / A.8.12 | Risco de exposição pública inadvertida de buckets |

> **Ação:** a TI (CIO/DevOps) deve remediar EXP-01…EXP-05 **imediatamente**, registrando a correção como
> evidência no nISO. Estes itens têm precedência sobre qualquer atividade de documentação.

### 3.2 NC MAIORES (bloqueiam certificação)

**NC-A — A.8.29 declarado sem lastro (corrigido).**
O controle de **teste de segurança em desenvolvimento e aceitação** estava `Implemented` no nISO, mas o
ambiente não possui SAST/DAST operante (sem pipeline CI/CD de aplicação; automação de build limitada a
infraestrutura; repositório de imagem de teste de segurança vazio). *Ação:* **rebaixado `Implemented →
In Progress` em 2026-08-27**, com justificativa registrada no nISO. *Cláusula:* 8.25–8.29, 7.5.

**NC-B — A.8.12 (DLP / prevenção de vazamento) não operante.**
Sem inventário/classificação automatizada de dados sensíveis, com exposição de rede e políticas de acesso
permissivas (ver EXP-01, EXP-03, EXP-04, EXP-05). Para uma plataforma de **biometria facial**, este é o
controle de maior materialidade. *Status nISO:* `Missing`. *Cláusula:* 8.12, 5.12, 8.3.

**NC-C — A.8.11 (mascaramento de dados) sem evidência de operação.**
Status `Missing` no nISO; a evidência de ambiente foi **inconclusiva** quanto a mascaramento/tokenização
de dados pessoais em repouso e em logs. *Cláusula:* 8.11.

**NC-D — A.8.16 (monitoramento) parcial.**
Logging existe e opera (A.8.15 confirmado), porém **sem alarmes/filtros de métrica configurados** — o
monitoramento é **passivo** (há registro, não há alerta). Um SGSI exige detecção, não só coleta.
*Status nISO:* `In Progress`. *Cláusula:* 8.16, 8.15.

**NC-E — SGSI (27001): 52 controles `In Progress` carecem de evidência objetiva.**
A maioria dos controles aplicáveis está implementada em status, mas o Stage 2 amostra **evidência de
operação**, não o rótulo. Cada `In Progress` precisa fechar com artefato citável e aprovação responsável.
*Cláusula:* 7.5, 9.1, 8.1.

**NC-F — Verificação independente (9.2) pendente.**
A auditoria interna 9.2 exige parte **independente** (não o consultor implementador). Pacote de
designação da **ness Processos e Tecnologia Ltda / Monica Yoshida Barbosa** elaborado (GOV-AUD-001),
**pendente de assinatura da declaração de imparcialidade + credenciais + aprovação da direção**.
*Cláusula:* 9.2, 9.3, 10.

### 3.3 NC MENORES / OBSERVAÇÕES

- **OBS-01 — ROPA de fluxo único:** confirmar se todos os fluxos de tratamento estão inventariados (além
  do biométrico: colaboradores/RH, logs, suporte). *Cláusula:* 27701 / LGPD Art. 37.
- **OBS-02 — Registro de riscos:** revisar inerente × residual e scores numéricos; reavaliar riscos que se
  apoiavam em controles agora rebaixados (A.8.29) ou `Missing` (A.8.11/8.12).
- **OBS-03 — Casing/vocabulário:** ~~status `Approved`; evidências `conforme`/`Conforme`.~~ **Padronizado**
  (POLICIES: campo Status normalizado; ver engagement.md).
- **OBS-04 — Transferência internacional:** **RESOLVIDO (NC-04 histórica):** dados em `sa-east-1`/Brasil —
  não há transferência internacional; enquadramento de SCC/us-east-1 retirado.
- **OBS-05 — Caminhos locais Windows** (`file:///c:/Users/...`) remanescentes em alguns artefatos — higiene.
- **OBS-06 — Aplicabilidade N/A:** revisar A.7.10/7.13/7.14 e demais N/A com justificativa genérica.

---

## 4. Cruzamento evidência de ambiente (AWS) × status nISO — controles A.8

| Controle | Status nISO (2026-08-27) | Evidência de ambiente | Veredito |
|---|---|---|---|
| A.8.8 — Gestão de vulnerabilidades técnicas | In Progress | Varredura contínua **ativa** | ✅ Coerente (fechar com evidência recorrente) |
| A.8.15 — Logging | In Progress → confirmado operante | Logs **coletados** | ✅ Coerente |
| A.8.16 — Monitoramento | In Progress | **Sem alarmes/filtros** — só coleta | ⚠️ Parcial (NC-D) |
| A.8.11 — Mascaramento | Missing | **Inconclusivo** | 🔶 Gap declarado (NC-C) |
| A.8.12 — DLP / prevenção de vazamento | Missing | **Não operante** + exposições | 🔴 Gap crítico (NC-B, EXP) |
| A.8.23 — Filtragem web | Not Applicable | Arquitetura nuvem/remota | ✅ N/A justificado |
| A.8.29 — Teste de segurança no SDLC | ~~Implemented~~ → **In Progress** | **Sem SAST/DAST** | 🔴 Rebaixado (NC-A) |

---

## 5. Plano de Ação detalhado

Prioridades: **P0** = exposições ao vivo (risco atual); **P1** = fechar núcleo técnico crítico + evidência;
**P2** = maturidade, cláusulas de gestão e verificação independente. Responsáveis são **sugestões** a
confirmar com a governança.

### P0 — Remediar exposições ao vivo (imediato)

| # | Ação | NC/EXP | Responsável | Critério de aceite |
|---|---|---|---|---|
| P0.1 | Restringir acesso administrativo remoto (remover exposição à internet pública) | EXP-01 | CIO/DevOps | Nenhuma regra de gestão aberta à internet pública |
| P0.2 | Habilitar MFA na conta-raiz e reduzir seu uso | EXP-02 | CIO | Raiz com MFA; acesso raiz auditado |
| P0.3 | Restringir política de acesso ao armazenamento (menor privilégio) | EXP-03 | CIO/DevOps | Política sem permissões amplas indevidas |
| P0.4 | Habilitar descoberta/classificação de dados sensíveis + bloqueio de acesso público no nível da conta | EXP-04/05 | CIO/DevOps | Ferramenta ativa; bloqueio público habilitado |

### P1 — Fechar o núcleo técnico crítico e produzir evidência

| # | Ação | NC | Responsável | Critério de aceite | Dependência |
|---|---|---|---|---|---|
| P1.1 | Implementar **DLP/A.8.12**: classificação, controle de exposição de rede, prevenção de vazamento | NC-B | CIO/DevOps | A.8.12 operante com evidência → `In Progress`→`Implemented` | P0 |
| P1.2 | Configurar **alarmes/filtros de métrica** (A.8.16): detecção ativa sobre os logs existentes | NC-D | CIO/DevOps | Alertas de segurança operando; A.8.16 → `Implemented` | — |
| P1.3 | Implementar **SAST/DAST no SDLC** (A.8.29): teste de segurança no pipeline de aplicação | NC-A | DevOps | Pipeline com testes de segurança; relatórios; A.8.29 → `Implemented` | — |
| P1.4 | Implementar/comprovar **mascaramento** (A.8.11) de dados pessoais em repouso e logs | NC-C | CIO/DevOps | A.8.11 com evidência → `Implemented` | — |
| P1.5 | Fechar os **52 `In Progress`** do 27001 com evidência objetiva + aprovação responsável | NC-E | CIO / donos | Cada `In Progress` com artefato citável no nISO | — |
| P1.6 | Confirmar cobertura do **ROPA** (todos os fluxos) e revisar **riscos** (residual/score) | OBS-01/02 | DPO/CIO | ROPA completo; matriz de risco com score | — |

### P2 — Gestão, maturidade e verificação independente

| # | Ação | NC | Responsável | Critério de aceite | Dependência |
|---|---|---|---|---|---|
| P2.1 | Fechar **A.5.35** (análise crítica independente) — `Planned` → operante | — | CIO | Análise crítica independente registrada | P1 |
| P2.2 | Evidenciar cláusulas de gestão **4–10** (contexto, liderança, planejamento, apoio, operação, avaliação, melhoria) | NC-E | Consultor + CIO | Artefatos de gestão 4–10 rastreáveis | — |
| P2.3 | **Auditoria interna 9.2 independente** — executar via ness/Monica (GOV-AUD-001), após assinaturas/credenciais | NC-F | Auditor independente | Relatório 9.2 independente; achados tratados (10.2) | P0, P1 |
| P2.4 | Higiene documental (caminhos locais, N/A genéricos, contagens) | OBS-05/06 | Consultor | Docs limpos; contagens conferem | — |
| P2.5 | Recomputar prontidão e decidir ida ao **Stage 1** | todas | Consultor | Sem exposições ao vivo; núcleo técnico fechado; IPC real | tudo acima |

---

## 6. Sequência recomendada e marcos

1. **Marco 0 (segurança operacional):** P0.1–P0.4 → exposições ao vivo remediadas. **Precede tudo.**
2. **Marco A (integridade) — ✅ CONCLUÍDO:** placar com lastro; declaração fictícia retirada; SoA
   reconciliado ao nISO; A.8.29 rebaixado.
3. **Marco B (núcleo técnico):** P1.1–P1.4 → A.8.11/8.12/8.16/8.29 fechados com evidência.
4. **Marco C (evidência + gestão):** P1.5–P1.6, P2.1–P2.2 → `In Progress` fechados; cláusulas 4–10.
5. **Marco D (verificação independente):** P2.3 → auditoria interna 9.2 **independente** (ness/Monica).
6. **Marco E (prontidão):** P2.5 → decisão informada de ida a Stage 1.

> **Independência (lei Aegis):** os itens de **implementação/adequação** são do consultor. A **auditoria
> interna 9.2** (Marco D) e o parecer de prontidão final **exigem sessão/agente independente** — não quem
> adequou. Toda escrita no nISO segue **proposta → aprovação humana → aplicação**.
