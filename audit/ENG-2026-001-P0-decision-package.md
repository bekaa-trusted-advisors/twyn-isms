# Pacote de Decisão P0 — ENG-2026-001 (pronto para aprovação em lote)

| Campo | Valor |
|---|---|
| **Engajamento / Contrato** | ENG-2026-001 / C-2026-08-18-01 |
| **Objetivo** | Restaurar a **integridade dos dados** do SoA (P0 do plano de ação) antes de qualquer implementação |
| **Natureza** | **Propostas** — nenhuma escrita no nISO foi feita. Cada bloco abaixo vira um lote de escritas que aplico **após sua aprovação** |
| **Direção das correções** | **Conservadora** — reduzir alegações sem lastro (nunca elevar sem evidência). Não fabrica conformidade. |
| **Reversível?** | Sim — `db:backup` + cada escrita é atômica |
| **Data** | 2026-08-19 |

> **Como usar:** revise cada bloco e responda "aprovo P0-A", "aprovo P0-B", etc. (ou ajuste).
> Ao aprovar, eu aplico as escritas correspondentes no nISO (`PUT /controls/{id}`), verifico e registro.
> **Enquanto você dormia, não escrevi nada no nISO** — apenas preparei este pacote.

---

## Bloco P0-A — Reconciliar status × maturidade (48 controles)

**Regra aplicada (conservadora):**
- `Missing` + maturidade ≥3 **com evidência** (41) → propor **`In Progress`** (mantém maturidade; *não* eleva a `Implemented` — isso exige verificação de evidência item a item).
- `Missing` + maturidade ≥3 **sem evidência** (7: A.8.8/8.11/8.12/8.15/8.16/8.23/8.29) → propor **maturidade `0`** (alinha à realidade `Missing`) até haver evidência.

> ⚠ Nenhum controle vira `Implemented` aqui. Elevar a `Implemented` é decisão P1, controle a controle, com evidência verificada.


| Controle | Status atual | Maturidade | Evidência? | Assinado? | Proposta (regra) |
|---|---|---:|:---:|:---:|---|
| A.5.10 Uso Aceitável de Informações e Outros A | `Missing` | 4 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.5.11 Devolução de Ativos | `Missing` | 3 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.5.12 Classificação da Informação | `Missing` | 3 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.5.13 Rotulagem da Informação | `Missing` | 3 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.5.14 Transferência de Informações | `Missing` | 3 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.5.16 Gestão de Identidades | `Missing` | 3 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.5.17 Informações de Autenticação | `Missing` | 3 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.5.18 Direitos de Acesso | `Missing` | 3 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.5.19 Segurança da Informação no Relacionamen | `Missing` | 5 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.5.20 Tratamento da Segurança da Informação n | `Missing` | 5 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.5.21 Gestão da Segurança da Informação na Ca | `Missing` | 3 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.5.22 Monitoramento, Análise Crítica e Gestão | `Missing` | 3 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.5.24 Planejamento e Preparação da Gestão de  | `Missing` | 4 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.5.26 Resposta a Incidentes de Segurança da I | `Missing` | 3 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.5.3 Segregação de Funções | `Missing` | 3 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.5.33 Proteção de Registros | `Missing` | 4 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.5.5 Contato com Autoridades | `Missing` | 3 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.5.6 Contato com Grupos Especiais de Interess | `Missing` | 3 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.5.7 Inteligência sobre Ameaças | `Missing` | 3 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.5.8 Segurança da Informação na Gestão de Pro | `Missing` | 3 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.5.9 Inventário de Informações e Outros Ativo | `Missing` | 4 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.6.3 Conscientização, Educação e Treinamento  | `Missing` | 4 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.6.5 Responsabilidades Pós-Desligamento ou Mu | `Missing` | 3 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.6.6 Acordos de Confidencialidade e Não Divul | `Missing` | 4 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.8.10 Exclusão de Informação | `Missing` | 5 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.8.11 Mascaramento de Dados | `Missing` | 4 | não | sim | → maturidade `0` (sem lastro) OU coletar evidência; recomendo zerar |
| A.8.12 Prevenção de Vazamento de Dados (DLP) | `Missing` | 4 | não | sim | → maturidade `0` (sem lastro) OU coletar evidência; recomendo zerar |
| A.8.13 Backup da Informação | `Missing` | 4 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.8.14 Redundância dos Recursos de Processamen | `Missing` | 3 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.8.15 Registros de Log | `Missing` | 5 | não | sim | → maturidade `0` (sem lastro) OU coletar evidência; recomendo zerar |
| A.8.16 Atividades de Monitoramento | `Missing` | 4 | não | sim | → maturidade `0` (sem lastro) OU coletar evidência; recomendo zerar |
| A.8.2 Direitos de Acesso Privilegiado | `Missing` | 3 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.8.20 Segurança de Redes | `Missing` | 3 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.8.21 Segurança dos Serviços de Rede | `Missing` | 3 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.8.23 Filtragem Web | `Missing` | 4 | não | sim | → maturidade `0` (sem lastro) OU coletar evidência; recomendo zerar |
| A.8.24 Uso de Criptografia | `Missing` | 4 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.8.25 Ciclo de Vida de Desenvolvimento Seguro | `Missing` | 4 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.8.26 Requisitos de Segurança em Aplicações | `Missing` | 4 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.8.27 Arquitetura de Sistemas Segura e Princí | `Missing` | 3 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.8.28 Codificação Segura | `Missing` | 4 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.8.29 Testes de Segurança em Desenvolvimento  | `Missing` | 4 | não | sim | → maturidade `0` (sem lastro) OU coletar evidência; recomendo zerar |
| A.8.3 Restrição de Acesso à Informação | `Missing` | 3 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.8.31 Separação dos Ambientes de Desenvolvime | `Missing` | 4 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.8.32 Gestão de Mudanças | `Missing` | 4 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.8.4 Acesso ao Código-Fonte | `Missing` | 3 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.8.5 Autenticação Segura | `Missing` | 4 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |
| A.8.8 Gestão de Vulnerabilidades Técnicas | `Missing` | 4 | não | sim | → maturidade `0` (sem lastro) OU coletar evidência; recomendo zerar |
| A.8.9 Gestão de Configuração | `Missing` | 3 | sim | sim | → `In Progress` (mantém maturidade); verificar evidência p/ eventual `Implemented` |

**Total Tabela A: 48 controles.**

---

## Bloco P0-B — Assinatura sem lastro (17 controles)

**Nuance de consultor (importante para sua decisão):**
- Os **9 controles `Not Applicable`** (A.7.1/7.2/7.3/7.4/7.5/7.6/7.8/7.11/7.12/8.22) assinados: para N/A, o "lastro" é a **justificativa documentada** (campo `description`), não prova de implementação. → Proposta: **garantir justificativa** e manter a aprovação (não retirar).
- Os **8 controles `Missing` assinados** (A.8.8/8.11/8.12/8.15/8.16/8.23/8.29) sem evidência: aprovação de um controle inexistente é insustentável. → Proposta: **retirar a aprovação** até haver implementação+evidência.


| Controle | Status | Assinado por | Evidência? | Proposta |
|---|---|---|:---:|---|
| A.7.1 Perímetros de Segurança Física | `Not Applicable` | CISO+CEO | não | Retirar aprovação até anexar evidência, OU anexar evidência objetiva |
| A.7.11 Utilidades de Suporte | `Not Applicable` | CISO+CEO | não | Retirar aprovação até anexar evidência, OU anexar evidência objetiva |
| A.7.12 Segurança do Cabeamento | `Not Applicable` | CISO+CEO | não | Retirar aprovação até anexar evidência, OU anexar evidência objetiva |
| A.7.2 Entrada Física | `Not Applicable` | CISO+CEO | não | Retirar aprovação até anexar evidência, OU anexar evidência objetiva |
| A.7.3 Proteção de Escritórios, Salas e Instala | `Not Applicable` | CISO+CEO | não | Retirar aprovação até anexar evidência, OU anexar evidência objetiva |
| A.7.4 Monitoramento da Segurança Física | `Not Applicable` | CISO+CEO | não | Retirar aprovação até anexar evidência, OU anexar evidência objetiva |
| A.7.5 Proteção Contra Ameaças Físicas e Ambien | `Not Applicable` | CISO+CEO | não | Retirar aprovação até anexar evidência, OU anexar evidência objetiva |
| A.7.6 Trabalho em Áreas Seguras | `Not Applicable` | CISO+CEO | não | Retirar aprovação até anexar evidência, OU anexar evidência objetiva |
| A.7.8 Localização e Proteção de Equipamentos | `Not Applicable` | CISO+CEO | não | Retirar aprovação até anexar evidência, OU anexar evidência objetiva |
| A.8.11 Mascaramento de Dados | `Missing` | CISO | não | Retirar aprovação até anexar evidência, OU anexar evidência objetiva |
| A.8.12 Prevenção de Vazamento de Dados (DLP) | `Missing` | CISO | não | Retirar aprovação até anexar evidência, OU anexar evidência objetiva |
| A.8.15 Registros de Log | `Missing` | CISO+CEO | não | Retirar aprovação até anexar evidência, OU anexar evidência objetiva |
| A.8.16 Atividades de Monitoramento | `Missing` | CISO | não | Retirar aprovação até anexar evidência, OU anexar evidência objetiva |
| A.8.22 Segregação de Redes | `Not Applicable` | CISO+CEO | não | Retirar aprovação até anexar evidência, OU anexar evidência objetiva |
| A.8.23 Filtragem Web | `Missing` | CISO | não | Retirar aprovação até anexar evidência, OU anexar evidência objetiva |
| A.8.29 Testes de Segurança em Desenvolvimento  | `Missing` | CISO | não | Retirar aprovação até anexar evidência, OU anexar evidência objetiva |
| A.8.8 Gestão de Vulnerabilidades Técnicas | `Missing` | CISO | não | Retirar aprovação até anexar evidência, OU anexar evidência objetiva |

**Total Tabela B: 17 controles assinados sem evidência.**

---

## Bloco P0-C — Saneamento de evidências


- **42 evidências `pending`** (a avaliar): AWS_GDPR_DPA.pdf, Contato ANPD e Cibercrim, Integração CERT.br e ANP, POL-ACP-001 - Politica d, POL-APP-001 - Requisitos, POL-EMP-001 - Politica d, POL-GOV-001 - Politica d, POL-GOV-001 Responsabili, POL-GOV-001 Segurança em, POL-HR-001 - Politica de, POL-IRP-001 - Politica d, POL-ISP-001 - Politica d, POL-SUP-001 - Politica d, POL-THR-001 Integração G, POL-TX-001 - Politica de, SGSI-SCOPE-001 - D
- **7 evidências órfãs** (control_id inexistente): A.5.1, A.5.19, A.5.24
- **Casing inconsistente:** {'pending': 42, 'conforme': 41, 'Conforme': 3, 'approved': 38} → padronizar para minúsculas.

**Propostas P0-C:**
1. Avaliar as **42 `pending`** (decidir conforme/não-conforme) — decisão de conteúdo, sua.
2. Remover/religar as **7 órfãs** (control_id `A.5.1`, `A.5.19`, `A.5.24` — provável id antigo; religar aos ids atuais `ctrl-a51`, etc.).
3. Padronizar `evaluation_status` para minúsculas (`Conforme`→`conforme`).

---

## Bloco P0-D — Privacidade 27701 (28 aplicáveis) — preparado, aguarda evidência

O control-set 27701:2025 foi semeado (31; 3 N/A já aplicados). Os **28 aplicáveis** têm **evidência
candidata mapeada** em `soa/SGPI-SoA-27701-2025.md`. A adequação (status/evidência) é **P1**, controle a
controle, pois exige verificar a evidência real — **não** é escrita cega. Sem decisão sua, permanece proposto.

---

## Matriz de aprovação (responda ao acordar)

| Bloco | O que aplico ao aprovar | Escritas nISO |
|---|---|---|
| **P0-A** | 41× `Missing→In Progress`; 7× maturidade→0 | 48 `PUT /controls/{id}` |
| **P0-B** | 9× garantir justificativa N/A; 8× retirar aprovação | 17 `PUT /controls/{id}` |
| **P0-C** | avaliar 42 pending; religar/remover 7 órfãs; padronizar casing | writes de evidência |
| **P0-D** | (P1) adequação dos 28 de privacidade | por controle, depois |

> **Independência:** tudo acima é adequação (consultor). A **auditoria interna 9.2** e o parecer de
> prontidão exigem sessão/agente **independente**. Nenhuma escrita no nISO ocorre sem sua aprovação.
