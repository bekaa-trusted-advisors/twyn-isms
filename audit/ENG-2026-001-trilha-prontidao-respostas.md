# Relatório de Prontidão e Respostas — Trilha de Implementação SGSIP · TWYN

| | |
|---|---|
| **Engajamento** | ENG-2026-001 (adequação ISO/IEC 27001:2022 + 27701:2025, papel Controlador) |
| **Data** | 2026-08-27 |
| **Fonte da verdade** | nISO (projeto `mr9c1qugo16zic2eko`), 41 fases da trilha |
| **Natureza** | Reconstrução da narrativa da trilha + **payload das notas por fase** para o nISO |

> ⚠️ **Reconstrução honesta.** Este documento reconstrói a narrativa da trilha a partir de artefatos
> **reais** (nISO + repo). Números vêm da **fonte da verdade** (nISO, 2026-08-27). Afirmações factuais que
> **ainda não têm artefato citável** estão marcadas **`[A CONFIRMAR]`** — não são apresentadas como
> conformidade. Onde não há fonte, é **gap declarado**, não resposta inventada.

> 🔒 A evidência de ambiente AWS (27/08/2026) é **RESTRITA**; citada aqui só em nível de controle.

---

## Placar de referência (nISO, 2026-08-27)

| Norma | Implemented | In Progress | Planned | Missing | N/A | Aplicáveis | % impl. (aplicáveis) |
|---|---:|---:|---:|---:|---:|---:|---:|
| ISO 27001:2022 (93) | 22 | 52 | 1 | 2 | 16 | 77 | ≈ 29% |
| ISO 27701:2025 (31) | 25 | 0 | 0 | 0 | 6 | 25 | 100% |
| **Total (124)** | **47** | **52** | **1** | **2** | **22** | **102** | **≈ 46%** |

- **IPC consolidado ≈ 46%** (47 implementados / 102 aplicáveis). *(Corrige o "≈66% / 52 de 79" da versão
  anterior, que se apoiava no placar de 18–19/ago.)*
- **2 Missing** (27001): **A.8.11** (Mascaramento), **A.8.12** (DLP). **1 Planned**: **A.5.35** (Análise
  Crítica Independente, a executar pela 9.2).

---

## 1. Bloco A — Mobilização, Diagnóstico e Contexto (Fases 0–6)

A viabilidade do SGSIP repousa sobre fundamentos estratégicos: engajamento da alta direção e delimitação
rigorosa do escopo. Para a TWYN, o mandato executivo e a clareza de onde a segurança se aplica são os
pilares de um sistema sustentável e auditável.

**Liderança e equipe (segregação de funções).** Patrocínio formal pelo **Kacio Giuliano Lopes (CEO)**
`[A CONFIRMAR: data 27/07/2026 — consta do registro da fase; confirmar em ata assinada]`. Estrutura:

- **Kacio Giuliano Lopes (CEO)** — Sponsor executivo; apetite a risco e orçamento.
- **Nizar Elouaer (CTO)** e **Marcelo Mascarenhas (DevOps Lead)** — braço executor (implementação técnica,
  hardening, engenharia de nuvem).
- **Humberto Oliveira (CIO / Resp. Segurança)** e **Rosa Correia (COO)** — gestão operacional (identidade,
  acessos, camada humana/RH).
- **Ricardo Esper (DPO-tech / Bekaa)** — supervisão normativa e assessoria; **sem privilégio de escrita/
  administração** em produção. **Não é CISO nem auditor.**
- **Monica Yoshida Barbosa (ness — auditoria independente 9.2)** — externa ao comitê, assegura a
  imparcialidade do requisito 9.2.

**Escopo e exclusões.** Escopo aprovado: *"Face ID Platform API + AWS Infrastructure (`sa-east-1`)"*,
processamento de biometria facial. Exclusão dos **controles físicos (A.7)** justificada pelo modelo 100%
remoto + nuvem (responsabilidade física transferida à AWS por responsabilidade compartilhada).
`[NOTA: o campo scope do projeto no nISO ainda diz "us-east-1" — correção de sistema pendente (NC-04); a
residência real do dado é sa-east-1/Brasil.]`

**Diagnóstico (IPC).** IPC atual **≈ 46%** (47 de 102 aplicáveis) — postura de sinceridade radical:
distingue realidade operacional de aspiração, evitando surpresa em auditoria.

## 2. Bloco B — Ativos, Riscos e SoA (Fases 7–14)

O dado biométrico é o "ativo de ouro"; a matriz de riscos direciona o investimento de segurança onde a
exposição é crítica.

**Fluxo do dado biométrico (Privacy by Design).**
1. **Trânsito:** canal cifrado `[A CONFIRMAR: TLS 1.3 — validar na configuração real]`.
2. **Processamento:** volátil em RAM com **expurgo imediato (0s)** da foto bruta após a vetorização
   (lastro no escopo/README).
3. **Armazenamento:** apenas o **vetor matemático** cifrado `[A CONFIRMAR: AES-256 no RDS — validar]`; a
   foto original **nunca é persistida** — minimização por padrão.

**Riscos.** `[A CONFIRMAR: "3 riscos reabertos por controles Missing" — reconferir no registro de riscos
atual; a aceitação de risco residual pela direção é temporária e condicionada ao cronograma de remediação.]`

**SoA (SGSI + SGPI).** Ver placar acima. **27001:** 22 impl · 52 In Progress · **2 Missing** · 16 N/A.
**27701 (Controlador):** **25 impl · 0 Missing · 6 N/A** (não é mais "projeção" — é o estado real).

## 3. Bloco C — Controles Organizacionais e Tecnológicos (Fases 15–20)

Dualidade: alta maturidade em gestão de pessoas (soft controls) × desafios de evidência técnica em nuvem
(hard controls).

**Pessoas e conscientização.** `[A CONFIRMAR: "100% dos colaboradores homologados na plataforma EVICERT" —
requer artefato (relação de conclusão); NDAs em vigência a evidenciar.]`

**Cloud e gaps técnicos (atualizado pela evidência de ambiente 27/08).** Não são mais "5 Missing": a
evidência avaliou os controles A.8 —
- **A.8.15 Logs** e **A.8.8 Vulnerabilidades**: operantes → `In Progress` (fechar com evidência recorrente).
- **A.8.16 Monitoramento**: **parcial** (logs sem alarmes/filtros) → `In Progress`.
- **A.8.23 Filtragem Web**: **N/A** justificado (nuvem/remoto).
- **A.8.11 Mascaramento**: **inconclusivo** → `Missing`.
- **A.8.12 DLP**: **não operante** + exposições de rede → `Missing`.
- **A.8.29 Teste de segurança no SDLC**: **rebaixado** `Implemented → In Progress` (sem SAST/DAST).

Restam **2 Missing** técnicos (A.8.11, A.8.12), ambos dependentes de **implementação real**.

## 4. Bloco D — Privacidade / SGPI sob ISO 27701 (Fases 21–27)

Como **Controladora** de dado sensível, a TWYN assume responsabilidade jurídica elevada. Base legal da
biometria: **LGPD Art. 11, II, 'g'** (prevenção à fraude / garantia de segurança do titular).

**Direitos do titular.** Canal do Encarregado **`dpo@t4isb.com`**; fluxo de DSAR (LGPD Art. 18) a
evidenciar em operação. **Soberania de dados:** operação e armazenamento no **Brasil (`sa-east-1`)** —
**não há transferência internacional**; o enquadramento de SCC/us-east-1 foi **retirado** (ROPA).

## 5. Bloco E — Operação, Auditoria Interna e Melhoria (Fases 28–33)

O rigor da fase de verificação (Check do PDCA) separa o sistema documental do sistema operacionalmente vivo.

**Incidentes e monitoramento.** `[A CONFIRMAR: POL-IRP-001 em vigência — evidenciar teste de mesa/simulação
regular; A.8.16 hoje é monitoramento passivo (sem alarmes) — ver Bloco C.]`

**Auditoria interna 9.2 (independente).** Designação de **Monica Yoshida Barbosa (ness)** — `GOV-AUD-001`.
Independência em relação ao comitê de implementação = credibilidade do relatório 9.2. **Pendente:**
assinatura da declaração de imparcialidade + credenciais + aprovação da direção. É o **gargalo formal**:
sem a 9.2 independente, não há parecer de prontidão — e ela **não** pode ser feita pela consultoria que
implementou.

## 6. Bloco F — Certificação e Encerramento (Fases 34–40)

**Stage 1 / Stage 2.** Condicionados à execução da **9.2** e à resolução dos **2 Missing** (A.8.11,
A.8.12) `[corrige "27 Missing" da versão anterior]` + fechamento dos 52 `In Progress` com evidência de
operação. Risco residual: auditor externo pode exigir maior **automação na extração de evidência** da AWS.

**Precede tudo:** remediar as **exposições ao vivo** identificadas na evidência de ambiente (risco atual;
detalhe no handoff RESTRITO). **Continuidade (BCP/DRP):** teste de resiliência exigido por grandes players/
reguladores (ex.: CAIXA) — evidenciar teste. Lições deste ciclo alimentam a melhoria contínua em 2027.

---

## Anexo — Notas por fase (payload proposto para o nISO)

> **Status técnico:** o campo `notes` das fases **não é gravável pela API do consultor** (o `PUT
> /projects/{id}/phases/{phase_id}` aceita `status`, mas **ignora `notes`** — retorna `{"ok":true}` sem
> persistir). Assim como o campo `owner` (liberado pelo nISO em 2026-08-26), a gravação de `notes` exige
> **liberação de sistema**. Até lá, estas notas ficam **staged aqui**; ao liberar, aplico o lote por API.
> **Aprovação humana** rege a aplicação (efeito externo no nISO do cliente).

| # | Fase | Nota proposta (concisa, fonte-verdade 2026-08-27) |
|---|---|---|
| 0 | Mobilização e Mandato | Patrocínio do CEO (Kacio) `[data a confirmar em ata]`; comitê e papéis definidos com segregação (executor/supervisão/auditoria). Mandato do SGSIP estabelecido. |
| 1 | Entrevista Executiva | Objetivos de negócio + apetite a risco capturados com a direção; certificação 27001+27701 como diferencial competitivo (biometria/CAIXA/ANPD). |
| 2 | Entrevistas por Trilha | `[PENDENTE de artefato]` — registrar por área (Eng./DevOps, Produto, Jurídico, RH, Suporte) os tratamentos e controles reais vs. aspiracionais. |
| 3 | Definição de Escopo | Escopo: Face ID Platform API + AWS `sa-east-1`, biometria facial. Exclusão de A.7 (100% remoto/nuvem) justificada. `[nISO scope ainda "us-east-1" — corrigir]` |
| 4 | Gap Assessment | Diagnóstico inicial reconciliado à fonte-verdade; IPC ≈46% (47/102). Integridade de dados restaurada (fim do "100% Audit Ready" fictício). |
| 5 | Governança e Papéis | RACI de SI/privacidade; sem cargo de CISO (decisão de governança) — responsabilidade no CIO (Humberto). DPO independente do CISO/consultor. |
| 6 | Contexto e Partes Interessadas | Questões internas/externas (4.1) e partes interessadas (4.2): CAIXA, ANPD, titulares, clientes → entradas do SGSIP. `[formalizar artefato 4.1/4.2]` |
| 7 | Inventário de Ativos e Dados | Ativo crítico = base biométrica (vetores); chaves, endpoints, RDS. `[completar inventário com proprietário/classificação por ativo]` |
| 8 | Mapeamento de Processos | Fluxo do dado biométrico fim-a-fim (coleta→vetorização→descarte); foto bruta não persistida (expurgo RAM 0s). |
| 9 | Riscos de Segurança | Metodologia ISO 27005. `[reintroduzir inerente×residual e score numérico; reavaliar riscos ligados a A.8.11/8.12/8.29]` |
| 10 | Riscos de Privacidade | Tratamento de biometria (Art. 11) — `[DPIA/RIPD a evidenciar]`; direitos dos titulares e salvaguardas. |
| 11 | Tratamento de Riscos | Decisão por risco + dono + prazo; aceitação de residual temporária e condicionada ao cronograma. `[formalizar aceitação pela direção]` |
| 12 | SoA do SGSI | 27001: 22 impl · 52 In Progress · 1 Planned · 2 Missing (A.8.11, A.8.12) · 16 N/A. Homologação (assinatura) da SoA pendente. |
| 13 | SoA do SGPI | 27701 (Controlador): 25 impl · 6 N/A · 0 Missing. Crosswalk 27001↔27701 aplicado. |
| 14 | Arquitetura Documental | Árvore de políticas ↔ controles; fonte-verdade = nISO + repo `twyn-isms`; versionamento por PR. |
| 15 | Controles Organizacionais (A.5) | Políticas organizacionais aprovadas; A.5.15/A.5.29 elevados a In Progress; A.5.35 Planned (via 9.2). |
| 16 | Controles de Pessoas (A.6) | `[A CONFIRMAR: treinamento (EVICERT?) 100% + NDAs — anexar relação de conclusão e termos]`. Processo disciplinar/offboarding a evidenciar. |
| 17 | Controles Físicos (A.7) | N/A justificado (equipe remota, infra 100% nuvem); responsabilidade compartilhada com a AWS documentada. |
| 18 | Controles Tecnológicos (A.8) | Evidência de ambiente 27/08 avaliada: A.8.8/8.15 operantes; A.8.16 parcial; A.8.23 N/A; A.8.11/8.12 Missing; A.8.29 rebaixado. |
| 19 | Desenvolvimento Seguro | A.8.29 rebaixado (sem SAST/DAST). `[implementar teste de segurança no SDLC + gestão de segredos + revisão de código]` |
| 20 | Cloud, DevOps e SRE | Arquitetura AWS `sa-east-1`; IaC (Terraform). `[endurecer configuração — ver exposições ao vivo; observabilidade/Config/Security Hub a evidenciar]` |
| 21 | Programa de Privacidade | Governança de privacidade + ROPA (fluxo biométrico); `[inventariar demais fluxos: RH, logs, suporte]`. |
| 22 | Privacy by Design | Minimização por padrão (foto não persistida); `[formalizar gatilho de DPIA e revisão de privacidade em mudanças]`. |
| 23 | Direitos dos Titulares (DSAR) | Canal do Encarregado `dpo@t4isb.com`; fluxo de DSAR (Art. 18). `[evidenciar atendimento e prazos]`. |
| 24 | Consentimento e Bases Legais | Base legal da biometria = Art. 11 II 'g' (não consentimento). Documentar por finalidade. |
| 25 | Retenção e Descarte | `[tabela de retenção por tipo de dado + descarte seguro/crypto-shredding a evidenciar]`. |
| 26 | Transferências e Compartilhamento | Sem transferência internacional (dados em `sa-east-1`/Brasil). Compartilhamento (CAIXA/operadores) sob DPA `[formalizar]`. |
| 27 | Fornecedores e Operadores | `[inventário de fornecedores críticos + qualificação (KYV) + cláusulas de segurança/privacidade]`. |
| 28 | Incidentes | `[A CONFIRMAR: POL-IRP-001 em vigência]`; detecção/contenção/notificação (ANPD/titulares) + pós-mortem; A.8.16 hoje passivo. |
| 29 | Treinamento | `[ementa, periodicidade, taxa de conclusão, certificados — anexar]`. |
| 30 | Monitoramento e Métricas | KPIs de SI/privacidade (9.1) `[definir/coletar]`; A.8.16 parcial (sem alarmes). |
| 31 | Auditoria Interna (9.2) | Designação ness/Monica (GOV-AUD-001), independente. Pendente: imparcialidade assinada + credenciais + aprovação da direção + execução. |
| 32 | Análise Crítica (9.3) | `[ata da análise crítica pela direção a produzir APÓS a 9.2, com entradas da 9.3.2]`. |
| 33 | Melhoria Contínua (10) | Tratamento de NC (10.2) com correção + ação corretiva; registro de NCs a manter. |
| 34 | Certificação Estágio 1 | `pending`. Condicionada à 9.2 + resolução de A.8.11/8.12 + fechamento dos In Progress. Organismo certificador a selecionar. |
| 35 | Certificação Estágio 2 | `pending`. Evidência de operação para amostragem; controles de maior risco de NC = técnicos (A.8). |
| 36 | Pós-Certificação | `pending`. Plano CAPA + ciclo de vigilância anual. |
| 37 | Gestão de Vulnerabilidades | `pending`. A.8.8 ativo; formalizar cadência de varredura + SLA de remediação por severidade + histórico. |
| 38 | Continuidade de Negócios | `pending`. `[BIA + BCP/DRP com RTO/RPO testados — evidenciar teste (exigência CAIXA)]`. |
| 39 | Segurança Física | `pending`. N/A por design (remoto/nuvem); camada física coberta pela AWS (responsabilidade compartilhada). |
| 40 | Encerramento do Ciclo | `pending`. Lições aprendidas + pacote de prontidão consolidado → entradas do ciclo 2027. |

---

## Pendências desta trilha (resumo honesto)

1. **`[A CONFIRMAR]`** — validar com artefato real: data de patrocínio (27/07/2026), treinamento EVICERT/
   100%, TLS 1.3, AES-256, "3 riscos reabertos", POL-IRP-001 em teste. Sem artefato → gap declarado.
2. **Fases sem conteúdo real** (2, 6–11, 21–30, 32, 37–40): a maioria precisa de **artefato de gestão** —
   não se preenche com texto inventado. As notas acima já marcam `[PENDENTE]`/`[A CONFIRMAR]`.
3. **Sistema:** liberar a gravação de `phases.notes` na API (como foi feito com `owner`) para eu aplicar o
   lote; e corrigir o campo `scope` do projeto (`us-east-1`→`sa-east-1`).
