# Banco de Perguntas da Trilha de Implementação (41 Fases) — TWYN · ENG-2026-001

**Objetivo:** roteiro de perguntas por fase para **localizar/recuperar as respostas reais** (entrevistas, decisões, artefatos) e, a partir delas, preencher a trilha no nISO **com base em fonte verdadeira**.

> ⚠️ Este documento traz **perguntas**, não respostas. As respostas devem vir de **artefatos reais** (atas, e-mails, exports, documentos). Onde não houver fonte, a fase é **gap declarado** — não se inventa resposta.

Escopo normativo: ISO/IEC 27001:2022 (SGSI) + ISO/IEC 27701:2025 (SGPI) · Papel: Controlador (LGPD Art. 11 II 'g').

---

## Bloco A — Mobilização e Diagnóstico (Fases 0–6)

### Fase 0 — Mobilização e Mandato
1. Quem patrocinou formalmente o SGSI/SGPI (alta direção) e em que data?
2. Qual o mandato/carta de abertura do projeto — objetivos, restrições, orçamento?
3. Quem compõe o comitê/equipe do projeto e com que papéis?

### Fase 1 — Entrevista Executiva
1. Quais os objetivos de negócio que a segurança/privacidade deve sustentar?
2. Qual o apetite a risco da direção e os ativos mais críticos (biometria)?
3. Há obrigações contratuais/regulatórias dirigentes (CAIXA, ANPD, clientes)?
4. Qual o prazo-alvo e a motivação da certificação (Stage 1/2)?

### Fase 2 — Entrevistas por Trilha
1. Por área (Eng./DevOps, Produto, Jurídico, RH, Suporte): quais processos tratam dados pessoais/biométricos?
2. Quais controles já existem de fato e quais são aspiracionais?
3. Onde estão as maiores dores/lacunas percebidas por cada trilha?

### Fase 3 — Definição de Escopo
1. Quais sistemas, ambientes (AWS `sa-east-1`), processos e unidades entram/saem do escopo?
2. Quais interfaces/exclusões e a justificativa de cada exclusão?
3. Qual a declaração de escopo oficial (texto) aprovada?

### Fase 4 — Gap Assessment
1. Para cada requisito (cláusulas 4–10) e controle do Anexo A: existe? opera? há evidência?
2. Qual a nota de maturidade por controle e o racional?
3. Quais os gaps priorizados e o esforço estimado?

### Fase 5 — Governança e Papéis
1. Qual a matriz RACI de segurança/privacidade (quem aprova, executa, é consultado)?
2. Como as responsabilidades de segurança estão atribuídas (sem exigir cargo "CISO")?
3. Como o Encarregado (DPO) se posiciona e reporta à direção?

### Fase 6 — Contexto e Partes Interessadas
1. Quais questões internas/externas afetam o SGSI/SGPI (cláusula 4.1)?
2. Quem são as partes interessadas e seus requisitos (4.2) — CAIXA, ANPD, titulares, clientes?
3. Como esses requisitos viram entradas do sistema de gestão?

---

## Bloco B — Ativos, Riscos e SoA (Fases 7–14)

### Fase 7 — Inventário de Ativos e Dados
1. Qual o inventário de ativos de informação (incl. bases biométricas, chaves, endpoints)?
2. Quem é o proprietário de cada ativo e sua classificação?
3. Onde os dados residem e transitam (buckets, RDS, KMS)?

### Fase 8 — Mapeamento de Processos
1. Quais os fluxos de dados pessoais fim-a-fim (coleta → vetorização → descarte)?
2. Quais sistemas/integrações tocam cada fluxo?
3. Onde há pontos de exposição/retenção?

### Fase 9 — Riscos de Segurança
1. Quais cenários de ameaça×vulnerabilidade sobre os ativos críticos?
2. Qual a metodologia (ISO 27005) e a escala de probabilidade/impacto?
3. Qual o risco inerente e o residual por cenário?

### Fase 10 — Riscos de Privacidade
1. Há DPIA/RIPD para o tratamento de biometria (Art. 11)?
2. Quais riscos aos direitos dos titulares e as salvaguardas?
3. Quais decisões automatizadas e seus controles (LGPD Art. 20)?

### Fase 11 — Tratamento de Riscos
1. Qual a decisão por risco (mitigar/aceitar/transferir/evitar) e o dono?
2. Qual o plano de tratamento com prazos e o risco residual aprovado?
3. Como a aceitação de risco residual foi formalizada pela direção?

### Fase 12 — SoA do SGSI
1. Para os 93 controles do Anexo A: aplicável ou não, com justificativa?
2. Qual o status e a evidência de cada controle aplicável?
3. Quem homologou a SoA?

### Fase 13 — SoA do SGPI (27701)
1. Quais controles do 27701 (Controlador) são aplicáveis e por quê?
2. Como o crosswalk 27001↔27701 foi tratado?
3. Qual a evidência por controle de privacidade?

### Fase 14 — Arquitetura Documental
1. Qual a árvore de políticas/procedimentos e a matriz política↔controle?
2. Qual o padrão de versionamento, aprovação e retenção documental?
3. Onde vive a fonte da verdade (nISO) e o repositório?

---

## Bloco C — Controles (Fases 15–20)

### Fase 15 — Controles Organizacionais (A.5)
1. Quais políticas organizacionais existem e estão aprovadas?
2. Como se dá gestão de fornecedores, ativos, classificação e acesso lógico?
3. Quais evidências operacionais sustentam cada controle?

### Fase 16 — Controles de Pessoas (A.6)
1. Há triagem, termos de sigilo/NDA, processo disciplinar e offboarding?
2. Qual a cobertura de conscientização/treinamento (SI e LGPD)?
3. Como se evidencia adesão (100% dos colaboradores)?

### Fase 17 — Controles Físicos (A.7)
1. Quais controles físicos aplicam-se (equipe remota, infra 100% nuvem)?
2. Quais são N/A e com que justificativa formal?
3. Como a responsabilidade compartilhada com a AWS está documentada?

### Fase 18 — Controles Tecnológicos (A.8)
1. Como operam MFA/IAM, criptografia (repouso/trânsito), logging, monitoramento?
2. Há DLP, mascaramento, gestão de vulnerabilidades, backup testado?
3. Quais exports do AWS comprovam a operação efetiva?

### Fase 19 — Desenvolvimento Seguro
1. Como funciona o SDLC seguro, SAST/DAST, revisão de código, gestão de segredos?
2. Há requisitos de segurança formalizados por feature?
3. Quais relatórios de teste de segurança existem?

### Fase 20 — Cloud, DevOps e SRE
1. Qual a arquitetura (VPC, contas, segregação de ambientes) e IaC?
2. Como se dá hardening, gestão de configuração e observabilidade?
3. Quais evidências de conformidade contínua (Config, Security Hub)?

---

## Bloco D — Privacidade / SGPI (Fases 21–27)

### Fase 21 — Programa de Privacidade
1. Qual a estrutura de governança de privacidade e o ROPA?
2. Como o ciclo de vida do dado é gerido (coleta→descarte)?
3. Quais métricas de privacidade são acompanhadas?

### Fase 22 — Privacy by Design
1. Como privacidade entra no design de novos produtos/mudanças?
2. Há gatilhos de DPIA e revisão de privacidade?
3. Como minimização e anonimização são aplicadas?

### Fase 23 — Direitos dos Titulares (DSAR)
1. Qual o procedimento de atendimento a DSAR e os prazos (LGPD Art. 18)?
2. Qual o canal oficial do Encarregado e sua operação?
3. Como se evidencia atendimento e registro das solicitações?

### Fase 24 — Consentimento e Bases Legais
1. Qual a base legal por finalidade (biometria = Art. 11 II 'g')?
2. Onde consentimento é/foi necessário e como é gerido?
3. Como a base legal é documentada e revista?

### Fase 25 — Retenção e Descarte
1. Qual a tabela de retenção por tipo de dado (templates, logs)?
2. Como se dá o descarte seguro/irreversível (NIST SP 800-88, crypto-shredding)?
3. Há dossiê comprobatório de purga?

### Fase 26 — Transferências e Compartilhamento
1. Há transferência internacional? (Dados em `sa-east-1`/Brasil → em princípio, não.)
2. Com quem há compartilhamento (CAIXA, operadores) e sob que salvaguardas?
3. Como acordos de operador/DPA estão formalizados?

### Fase 27 — Fornecedores e Operadores
1. Qual o inventário de fornecedores críticos e a qualificação (KYV)?
2. Há cláusulas de segurança/privacidade e monitoramento (SOC, ISO)?
3. Como se revisa o desempenho dos fornecedores?

---

## Bloco E — Operação, Auditoria e Melhoria (Fases 28–33)

### Fase 28 — Incidentes
1. Qual o plano de resposta a incidentes (IRP) e os papéis?
2. Como se dá detecção, contenção, notificação (ANPD/titulares) e pós-mortem?
3. Há registro/histórico de incidentes e lições?

### Fase 29 — Treinamento
1. Qual a ementa, a periodicidade e a taxa de conclusão?
2. Como se avalia aproveitamento (nota mínima)?
3. Onde estão os certificados/atas?

### Fase 30 — Monitoramento e Métricas
1. Quais KPIs/indicadores de SI e privacidade são medidos (cláusula 9.1)?
2. Qual a fonte de dados e a periodicidade?
3. Como os resultados alimentam decisões?

### Fase 31 — Auditoria Interna (9.2)
1. Qual o programa de auditoria (escopo, critérios, frequência)?
2. Quem executa, assegurando independência/imparcialidade?
3. Quais achados, não conformidades e o relatório?

### Fase 32 — Análise Crítica (9.3)
1. Houve análise crítica pela direção e quais as entradas (9.3.2)?
2. Quais as decisões/saídas (recursos, melhorias)?
3. Onde está a ata?

### Fase 33 — Melhoria Contínua (10)
1. Como não conformidades são tratadas (correção + ação corretiva, 10.2)?
2. Qual o registro de NCs e o status de tratamento?
3. Como se evidencia a melhoria contínua (10.1)?

---

## Bloco F — Certificação e Encerramento (Fases 34–40)

### Fase 34 — Certificação Estágio 1
1. O organismo certificador (acreditado) foi selecionado?
2. A documentação está pronta para a análise documental?
3. Quais lacunas o Stage 1 apontaria?

### Fase 35 — Certificação Estágio 2
1. As evidências de operação estão disponíveis para amostragem?
2. Quais controles têm maior risco de NC em campo?
3. Qual a estratégia de resposta a achados?

### Fase 36 — Pós-Certificação
1. Qual o plano de ação corretiva (CAPA) pós-auditoria?
2. Como se mantém o ciclo (vigilância anual)?
3. Quais melhorias foram priorizadas?

### Fase 37 — Gestão de Vulnerabilidades
1. Qual a ferramenta/cadência de varredura e o SLA de remediação por severidade?
2. Como pentest/relatórios são geridos?
3. Onde está o histórico de remediação?

### Fase 38 — Continuidade de Negócios
1. Há BIA, BCP/DRP com RTO/RPO definidos e testados?
2. Como a continuidade da SI é assegurada em interrupção (A.5.29/5.30)?
3. Onde estão os registros de teste?

### Fase 39 — Segurança Física
1. Quais controles físicos aplicam-se ou são N/A (equipe remota/nuvem)?
2. Como a camada física da AWS é coberta pela responsabilidade compartilhada?
3. Qual a justificativa formal das exclusões?

### Fase 40 — Encerramento do Ciclo
1. O ciclo do SGSI/SGPI foi encerrado com lições aprendidas?
2. Quais entradas alimentam o próximo ciclo?
3. Onde está o pacote de prontidão consolidado?

---

## Como usar (fluxo honesto)
1. Para cada fase, **busque a resposta real** (ata, e-mail, export, documento). 
2. Traga o artefato → a consultoria **reconstrói a nota** no nISO **a partir dele** (referência citável).
3. **Sem artefato = gap declarado.** Se a atividade é necessária à certificação, **refaça-a de verdade** (a entrevista/assessment real) — não se simula.
