# TWYN Face ID Platform — Postura de Segurança & Prontidão Global

> **Repositório de Adequação Documental e Auditoria de Conformidade**  
> Alinhado às normas **ABNT NBR ISO/IEC 27001:2022** (SGSI) e **ABNT NBR ISO/IEC 27701:2019** (SGPI).

Este repositório consolida o arcabouço documental e o registro de evidências coletadas para suportar a certificação do Sistema de Gestão da Segurança da Informação e Privacidade (SGSIP) da Twyn.

---

## 📊 Status de Prontidão Global (IPC)

> **Reconciliação ENG-2026-001 (2026-08-18):** o índice abaixo foi recalculado a
> partir do estado real do `SOA.md`. O valor de "100% / Audit Ready" anterior não
> se sustentava perante os próprios artefatos. Ver `audit/ENG-2026-001-reconciliation.md`.

* **Índice de Prontidão de Conformidade (IPC):** **≈ 66%** (52 implementados / 79 aplicáveis)
* **Distribuição do SoA (93 controles):** 49 `Implemented` · 3 normalizados p/ `Implemented` · 27 `Missing` · 14 `Not Applicable`
* **Status:** `Em Adequação` — **não pronto para certificação**; reconciliação de status pendente (nISO)
* **Controles em aberto:** 27 · **Inconsistências sinalizadas:** ver `⚠` no `SOA.md`
* **Última Atualização (reconciliação):** 2026-08-18

---

## 🎯 Escopo do SGSIP

O escopo do SGSIP abrange toda a infraestrutura técnica e de governança operacional associada ao processamento e armazenamento biométrico:

> **Escopo Oficial (nISO):**  
> *"Face ID Platform API + AWS Infrastructure (us-east-1) - Processamento de Biometria Facial (Vetorização Matemática Irreversível sob LGPD Art. 11, II, 'g')"*

As operações incluem:
- **Segurança Lógica:** APIs públicas expostas em nuvem AWS (us-east-1).
- **Tratamento de Dados Pessoais Sensíveis:** Vetorização matemática de dados biométricos faciais, com expurgo imediato (0s) das fotos brutas em memória RAM, em conformidade com as diretrizes de privacidade da LGPD.
- **Governança Corporativa:** Políticas, conscientização de colaboradores, gestão de fornecedores por Tiers, e resposta estruturada a incidentes.

---

## 👥 Equipe de Governança do SGSIP

| Nome | Cargo Corporativo | Papel no SGSIP | Contato |
|---|---|---|---|
| **Kacio Lopes** | CEO | Sponsor Executivo / Aprovador Geral | `kacio@twyn.com` |
| **Nizar Elouaer** | CTO | Liderança de Segurança Lógica e Infraestrutura | `nizar@twyn.com` |
| **Ricardo Esper** | DPO / Consultor | Encarregado de Privacidade (DPO) e Governança | `privacy@t4isb.com` |
| **Rosa Correia** | COO | Liderança de RH e Operações | `rosa@twyn.com` |
| **Marcelo Mascarenhas** | DevOps Lead (T4ISB) | Engenharia de Nuvem, Backup e Segurança de Rede | `marcelo.mascarenhas@t4isb.com` |

---

## 📁 Estrutura de Pastas de Conformidade

Este repositório segue estritamente a árvore canônica de GRC:

* **[SOA.md](file:///c:/Users/resper/OneDrive/Área de Trabalho/DESENVOLVIMENTO/twyn-isms/SOA.md):** Declaração de Aplicabilidade (93 controles ISO 27001 + 27701).
* **[RISKS.md](file:///c:/Users/resper/OneDrive/Área de Trabalho/DESENVOLVIMENTO/twyn-isms/RISKS.md):** Registro de Riscos baseados na ISO 27005.
* **[ROPA.md](file:///c:/Users/resper/OneDrive/Área de Trabalho/DESENVOLVIMENTO/twyn-isms/ROPA.md):** Registro de Atividades de Tratamento de Dados Pessoais (LGPD).
* **[POLICIES/](file:///c:/Users/resper/OneDrive/Área de Trabalho/DESENVOLVIMENTO/twyn-isms/POLICIES/):** Políticas e procedimentos de segurança por controle Annex A.
* **[EVIDENCE/](file:///c:/Users/resper/OneDrive/Área de Trabalho/DESENVOLVIMENTO/twyn-isms/EVIDENCE/):** Pasta física com as 41 evidências auditáveis assinadas e catalogadas.
