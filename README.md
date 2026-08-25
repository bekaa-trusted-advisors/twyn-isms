# TWYN Face ID Platform — Postura de Segurança & Prontidão Global

> **Repositório de Adequação Documental e Auditoria de Conformidade**  
> Alinhado às normas **ABNT NBR ISO/IEC 27001:2022** (SGSI) e **ABNT NBR ISO/IEC 27701:2025** (SGPI).

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
> *"Face ID Platform API + AWS Infrastructure (sa-east-1) - Processamento de Biometria Facial (Vetorização Matemática Irreversível sob LGPD Art. 11, II, 'g')"*

As operações incluem:
- **Segurança Lógica:** APIs públicas expostas em nuvem AWS (sa-east-1).
- **Tratamento de Dados Pessoais Sensíveis:** Vetorização matemática de dados biométricos faciais, com expurgo imediato (0s) das fotos brutas em memória RAM, em conformidade com as diretrizes de privacidade da LGPD.
- **Governança Corporativa:** Políticas, conscientização de colaboradores, gestão de fornecedores por Tiers, e resposta estruturada a incidentes.

---

## 👥 Equipe de Governança do SGSIP

| Nome | Cargo Corporativo | Papel no SGSIP | Contato |
|---|---|---|---|
| **Kacio Lopes** | CEO | Sponsor Executivo / Aprovador Geral | `kacio@twyn.com` |
| **Nizar Elouaer** | CTO | Liderança de Segurança Lógica e Infraestrutura | `nizar@twyn.com` |
| **Bekaa Tecnologia Ltda** (CNPJ 28.811.817/0001-69) | DPO / Encarregado terceirizado | Encarregado pelo Tratamento de Dados Pessoais — LGPD Art. 41, DPO-as-a-Service (ref. GOV-DPO-001; resp. técnico **Ricardo Esper**). Papel de assessoria/supervisão — auditoria (interna 9.2 e de certificação) permanece com partes independentes | `dpo@twyn.com` |
| **Humberto Oliveira** | CIO / Líder de Operações de Segurança | Operações de segurança, identidade e acesso (papéis internos — **não** acumula o Encarregado/DPO) | _(e-mail a preencher)_ |
| **Ricardo Esper** | Consultor externo (Aegis) + Responsável técnico do DPO (via Bekaa) | Consultoria de adequação ISO 27001/27701 (ENG-2026-001) e responsável técnico do Encarregado (Bekaa). **Não é auditor** (a auditoria interna 9.2 é de parte independente) **nem CISO** | `dpo@twyn.com` |
| **Rosa Correia** | COO | Liderança de RH e Operações | `rosa@twyn.com` |
| **Marcelo Mascarenhas** | DevOps Lead (T4ISB) | Engenharia de Nuvem, Backup e Segurança de Rede | `marcelo.mascarenhas@t4isb.com` |

---

## 📁 Estrutura de Pastas de Conformidade

Este repositório segue estritamente a árvore canônica de GRC:

* **[SOA.md](SOA.md):** Declaração de Aplicabilidade (93 controles ISO 27001 + 27701).
* **[RISKS.md](RISKS.md):** Registro de Riscos baseados na ISO 27005.
* **[ROPA.md](ROPA.md):** Registro de Atividades de Tratamento de Dados Pessoais (LGPD).
* **[POLICIES/](POLICIES/):** Políticas e procedimentos de segurança por controle Annex A.
* **[EVIDENCE/](EVIDENCE/):** Pasta física com as 41 evidências auditáveis assinadas e catalogadas.
