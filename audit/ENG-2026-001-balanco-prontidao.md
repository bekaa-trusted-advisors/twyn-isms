# Balanço de Prontidão — ENG-2026-001 (TWYN Face ID Platform)

> **Documento de trabalho do consultor.** Retrato do estado da adequação em **2026-08-24**. **Não é
> parecer de conformidade nem de certificação** — a prontidão para o Stage 1 depende da **auditoria
> interna independente (cláusula 9.2)**, que por regra não é executada por quem implementou.

**Escopo:** ISO/IEC 27001:2022 (SGSI) + ISO/IEC 27701:2025 (SGPI) · **Fonte da verdade:** nISO
(`mr9c1qugo16zic2eko`).

## 1. Placar atual

**Segurança — ISO 27001 (93 controles do Anexo A):**

| Estado | Qtd |
|---|---|
| Implemented | 20 |
| In Progress (implementados, pendente de vínculo/aprovação) | 48 |
| Not Applicable (justificado) | 15 |
| Planned (A.5.35 — depende da auditoria 9.2) | 3 |
| **Missing** | **7** |

**Privacidade — ISO 27701 (31 controles, Controlador):**

| Estado | Qtd |
|---|---|
| Implemented | 24 |
| Not Applicable (justificado) | 3 |
| **Missing** | **4** |

> Comparativo: os controles "faltando" caíram de **28 → 7** (27001) e de **28 → 4** (27701) neste
> engajamento. Toda elevação cita o documento de lastro; a verificação de operação efetiva cabe à 9.2.

## 2. O que a consultoria entregou

- **Governança:** DPO terceirizado (Bekaa Tecnologia Ltda, resp. técnico Ricardo Esper; auditoria 9.2 por parte independente); Ricardo Esper como consultor apenas; função de segurança atribuída ao cargo do CIO
  (Humberto). Ato de nomeação e Contrato de DPO **prontos para assinatura**.
- **Normas:** migração do SGPI para 27701:2025; SoA e SGPI-SoA reconciliados contra o nISO.
- **Adequação:** 24 controles de privacidade e 34 de segurança documentados/elevados com lastro; 15
  políticas/procedimentos de segurança redigidos; correções de aplicabilidade (nuvem, remoto, teste).
- **Integridade:** aprovações de CISO sem lastro **desaprovadas**; canal DSAR unificado; títulos e
  papéis padronizados.
- **Encaminhamentos:** consolidado único de tarefas de UI do nISO; handoff de exports AWS; requisito
  de plataforma ao nISO.

## 3. O que falta (quase tudo é do lado do cliente)

| # | Item | Responsável |
|---|---|---|
| 1 | **Sessão de UI do nISO** (re-vincular evidências dos 7+4 Missing; corrigir aplicabilidade; limpar `ciso_approved_by`; higiene do store) — ver `nISO-UI-tarefas-consolidado.md` | Operador do nISO |
| 2 | **Exports do AWS** (Macie/DLP, CloudTrail, GuardDuty, filtragem web) — ver `handoff-OPS-export-AWS.md` | DevOps (Marcelo) |
| 3 | **Assinaturas:** Ato do DPO (CEO), Contrato DPO-as-a-Service, homologação da SoA; anexar Cartão CNPJ | CEO / partes |
| 4 | **Designar a parte independente** para a auditoria interna 9.2 (≠ Bekaa) | Direção |
| 5 | **Auditoria interna 9.2** controle a controle contra evidência; tratar não conformidades (10.2) | Parte independente (issue #17) |

## 4. Caminho até o Stage 1

1. Cliente executa **(1)** e **(2)** → derruba os 7+4 Missing e vincula as evidências.
2. **(3)** assinaturas → instrumentos de governança em vigor.
3. **(5)** auditoria interna 9.2 por parte independente → **parecer de prontidão** para o Stage 1.
4. Só então: **agendar o organismo certificador** (Stage 1 documental → Stage 2 em campo).

> A etapa **5** é o pré-requisito formal e o gargalo: sem a 9.2 independente, não há parecer de
> prontidão — e ela não pode ser feita pelo consultor de adequação.
