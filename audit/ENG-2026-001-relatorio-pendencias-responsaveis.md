# Relatório de Pendências para o Stage 1 — TWYN Face ID Platform

| | |
|---|---|
| **Engajamento** | ENG-2026-001 (adequação ISO/IEC 27001:2022 + 27701:2025) |
| **Data** | 2026-08-27 |
| **Substitui** | versão 2026-08-26 (placar 23/47/5/3/15 e Bloco A pré-evidência de ambiente) |
| **Fonte da verdade** | nISO (projeto `mr9c1qugo16zic2eko`) — `SOA.md` do repo reconciliado (0 divergências) |
| **Natureza** | Relatório de **prontidão/pendências** — **não** é parecer de conformidade nem de certificação |

> 🔒 **Confidencialidade.** A evidência de ambiente AWS (coleta 27/08/2026) é **RESTRITA** e **não é
> versionada** neste repositório público. Os achados aparecem aqui **em nível de controle**; os detalhes
> técnicos (conta, IPs, portas, regras, políticas) ficam no **handoff RESTRITO** para a TI e no nISO.

---

## 1. Onde estamos (placar atual — 2026-08-27)

| Norma | Implemented | In Progress | Missing | Planned | N/A |
|---|---|---|---|---|---|
| **ISO 27001 (93)** | 22 | 52 | **2** | 1 | 16 |
| **ISO 27701 (31)** | 25 | — | **0** | — | 6 |

> Privacidade (27701) segue **sem Missing**. Segurança (27001) tem agora **2 Missing técnicos**
> (A.8.11, A.8.12) e **52 In Progress** (implementados, mas com a **evidência de operação** a verificar).
> **Mudança material do dia:** a evidência de ambiente entregue pela TI foi avaliada e gerou 4 correções
> de status no nISO (§2, Bloco A) — inclusive o **rebaixamento de A.8.29** (`Implemented → In Progress`).

---

## 2. Pendências, responsável e o que fecha cada uma

### 🔴 Bloco 0 — Exposições ao vivo (tratamento IMEDIATO, precede tudo)
**Responsável: Tecnologia / DevOps — Marcelo Mascarenhas · Nizar Elouaer (CTO)**
*(apoio: Humberto Oliveira — CIO / Resp. Segurança)*

A evidência de ambiente revelou condições de **risco operacional atual** sobre a plataforma de biometria.
Não são gaps documentais — são exposições reais em produção. **Passos necessários (genéricos; specifics no
handoff RESTRITO):**

| # | Condição (nível de controle) | Passo necessário | Controle |
|---|---|---|---|
| EXP-01 | Acesso admin remoto exposto à internet pública | Remover regras de gestão abertas ao público; restringir a faixas conhecidas/VPN | A.8.20/8.22 |
| EXP-02 | Acesso raiz da nuvem sem 2FA | Habilitar MFA na raiz; minimizar/segregar o uso da raiz | A.5.15/8.5 |
| EXP-03 | Política de acesso a storage permissiva | Aplicar menor privilégio na política do recurso de armazenamento | A.8.3/5.15 |
| EXP-04 | Descoberta/classificação de dados sensíveis desabilitada | Habilitar a ferramenta de descoberta de dados; revisar findings | A.8.12/5.12 |
| EXP-05 | Sem bloqueio de acesso público no nível da conta de storage | Habilitar bloqueio público na conta | A.8.3/8.12 |

> **Aceite:** cada item remediado, com a correção registrada como evidência no nISO. Estes têm precedência
> sobre qualquer atividade de documentação.

### 🔴 Bloco A — Controles técnicos: evidência de ambiente avaliada (o que mudou)
**Responsável: Tecnologia / DevOps — Marcelo Mascarenhas · Nizar Elouaer (CTO)**
*(apoio: Humberto Oliveira — CIO / Resp. Segurança)*

A evidência AWS **chegou e foi avaliada** — não é mais "aguardando export". Estado por controle e o passo
que o fecha:

| Controle | Estado após evidência | Status nISO | Passo necessário para fechar (`→ Implemented`) |
|---|---|---|---|
| **A.8.15** — Logs | ✅ Operante (logs coletados) | In Progress | Anexar evidência recorrente (retenção + validação de integridade) e verificação 9.2 |
| **A.8.8** — Vulnerabilidades | ✅ Varredura ativa | In Progress | Anexar evidência de varredura recorrente + **SLA de remediação** por severidade |
| **A.8.23** — Filtragem Web | ✅ N/A justificado (nuvem/remoto) | **Not Applicable** | Fechado — exclusão a validar na 9.2 |
| **A.8.16** — Monitoramento | ⚠️ **Parcial** — logs sem alarmes/filtros | In Progress | **Configurar alarmes/filtros de métrica** (detecção ativa) sobre os logs existentes |
| **A.8.11** — Mascaramento | 🔶 **Inconclusivo** | **Missing** | Implementar/comprovar mascaramento de dados pessoais em repouso e em logs |
| **A.8.12** — DLP | 🔴 **Não operante** + exposições | **Missing** | Classificação de dados + controle de exposição de rede + prevenção de vazamento (ver Bloco 0) |
| **A.8.29** — Teste de segurança no SDLC | 🔴 **Sem SAST/DAST** | **In Progress** *(rebaixado de Implemented)* | Implementar SAST/DAST no pipeline de aplicação + relatórios de teste |

> Restam **2 Missing** (A.8.11, A.8.12) — ambos dependem de **implementação real** (não só de export). Os
> relatórios de gestão da CAIXA (REL-18.18/18.19) podem **acompanhar** como corroboração, mas não
> substituem a operação efetiva do controle.

### 🟠 Bloco B — 52 controles `In Progress` (evidência de operação a verificar)
**Responsável: Auditoria interna 9.2 — ness / Monica Yoshida Barbosa**
*(dona do programa: direção da TWYN)*

- São controles **implementados e documentados**, mas cuja **operação efetiva** precisa ser **verificada**
  para subir a `Implemented`. Quem faz essa verificação é a **auditoria 9.2** — não a consultoria (vedação
  à autorrevisão). **Passo:** amostragem de evidência por controle → parecer da 9.2 → elevação de status.

### 🟡 Bloco C — 1 controle `Planned`
**Responsável: conforme o controle**

| Controle | Responsável | Passo necessário |
|---|---|---|
| **A.5.35** — Análise Crítica Independente | ness / Monica (9.2) | Executado **pela** auditoria 9.2 — sai de `Planned` quando a 9.2 rodar |

> *A.5.15 (Controle de Acesso) e A.5.29 (Continuidade) já foram elevados de `Planned` → `In Progress` em
> 2026-08-26 (tinham política + maturidade). Não são mais pendência de status.*

### 🟢 Bloco D — Governança e assinaturas
**Responsável: Alta direção**

| Item | Responsável | Documento | Passo necessário |
|---|---|---|---|
| Assinar o **Ato de Nomeação do DPO** | **Kacio Giuliano Lopes** (CEO) | `GOV-DPO-001` | Assinatura do CEO |
| Anexar **contrato de DPO assinado** + **Cartão CNPJ** da Bekaa | DPO (Bekaa) / Jurídico | `GOV-DPO-002` | Anexar documentos |
| Homologar (assinar) a **SoA** | Resp. Segurança (Humberto) + CEO | `SOA.md` | Assinatura conjunta |
| **Análise Crítica pela Direção** (cl. 9.3) | CEO + direção | ata a produzir | Realizar **após** a 9.2, com as entradas da 9.3.2 |

### 🔵 Bloco E — Auditoria interna 9.2 (o gargalo formal)
**Responsável: ness / Monica Yoshida Barbosa** *(designação `GOV-AUD-001`)*

| Passo | Responsável |
|---|---|
| Assinar a **Declaração de Imparcialidade** + anexar credenciais | ness / Monica |
| Aprovar a designação | Direção TWYN |
| **Executar** a auditoria (27001+27701) e emitir relatório | ness / Monica |
| Tratar **não conformidades** (cl. 10.2) | Direção + responsáveis dos controles |

> A pré-avaliação de prontidão (dry-run) já existe e serve de insumo; **não** substitui esta 9.2 formal e
> independente perante o organismo certificador.

### ⚪ Bloco F — Higiene de evidências no nISO (não bloqueia o Stage 1)
**Responsável: DPO / operador do nISO** *(apoio da consultoria)*

- Evidências `pending` — avaliar conforme/não-conforme (julgamento de conteúdo). *(contagem a reapurar)*
- Vínculos "quebrados" (relatórios simulados de auditoria) — mantidos órfãos **de propósito** (simulação
  da consultoria, não revisão independente).
- Órfãs legítimas (artefatos de sistema de gestão) — sem controle do Anexo A; por design.
- Procedência: pedido de correção do `uploaded_by` (`consultant@ness.io` → uploader real) enviado ao
  admin do nISO (a API do consultor não grava esse campo).

---

## 3. Matriz de responsáveis (resumo)

| Responsável | Papel | O que está na mão dele |
|---|---|---|
| **Marcelo Mascarenhas** | DevOps Lead (T4ISB) | Bloco 0 (exposições) + Bloco A (implementação/exports do AWS) |
| **Nizar Elouaer** | CTO / Diretor Técnico | Bloco 0/A — liderança técnica |
| **Humberto Oliveira** | CIO / Resp. Segurança | Bloco 0/A (apoio), D (homologar SoA) |
| **Kacio Giuliano Lopes** | CEO | Bloco D — assinaturas de alta direção; 9.3 |
| **Enes F. Degasperi** | Diretor Financeiro / Procurador | Bloco D — contrato/cartão CNPJ (jurídico) |
| **DPO — Bekaa (Ricardo Esper, resp. técnico)** | Encarregado | Bloco D/F — anexos e higiene |
| **ness / Monica Yoshida Barbosa** | Auditoria interna 9.2 | Bloco B, C (A.5.35), E — a auditoria |
| **Consultoria (Aegis/Bekaa)** | Apoio | Vincular evidências no nISO; **não** audita |

---

## 4. Caminho crítico até o Stage 1

0. **Bloco 0** (TI) → **remediar as exposições ao vivo** (EXP-01…05). Precede tudo — é risco atual.
1. **Bloco A** (TI) → fechar **A.8.11 e A.8.12** (implementação real) e reforçar A.8.16/8.29 com evidência.
2. **Bloco D** (direção) → instrumentos de governança em vigor (Ato DPO, contrato, SoA homologada).
3. **Bloco E** (ness/Monica) → executa a **9.2** → verifica os 52 `In Progress` e converte em `Implemented`
   verificado; emite o **parecer de prontidão**.
4. **Bloco D (9.3)** → Análise Crítica pela Direção com as saídas da 9.2.
5. Só então: **agendar o organismo certificador** (Stage 1 documental → Stage 2 em campo).

> O **Bloco E é o gargalo formal**: sem a auditoria 9.2 independente, não há parecer de prontidão — e ela
> **não** pode ser feita pela consultoria que implementou. O **Bloco 0 é o gargalo de segurança**: as
> exposições ao vivo devem cair **já**, independentemente do cronograma de certificação.
