# Balanço de Prontidão — ENG-2026-001 (TWYN Face ID Platform)

> **Documento de trabalho do consultor.** Retrato do estado da adequação em **2026-08-26**. **Não é
> parecer de conformidade nem de certificação** — a prontidão para o Stage 1 depende da **auditoria
> interna independente (cláusula 9.2)**, que por regra não é executada por quem implementou.

**Escopo:** ISO/IEC 27001:2022 (SGSI) + ISO/IEC 27701:2025 (SGPI) · **Fonte da verdade:** nISO
(`mr9c1qugo16zic2eko`).

## 1. Placar atual

**Segurança — ISO 27001 (93 controles do Anexo A):**

| Estado | Qtd |
|---|---|
| Implemented | 23 |
| In Progress (implementados, pendente de vínculo/evidência de operação) | 47 |
| Not Applicable (justificado) | 15 |
| Planned (A.5.35 — depende da auditoria 9.2) | 3 |
| **Missing** | **5** |

**Privacidade — ISO 27701 (31 controles, Controlador):**

| Estado | Qtd |
|---|---|
| Implemented | 25 |
| Not Applicable (justificado) | 6 |
| **Missing** | **0** |

> Comparativo: os controles "faltando" caíram de **28 → 5** (27001) e de **28 → 0** (27701) neste
> engajamento. Toda elevação cita o documento de lastro; a verificação de operação efetiva cabe à 9.2.
> Os **5 Missing** do 27001 são exclusivamente técnicos e dependem de export do AWS: **A.8.11**
> (mascaramento), **A.8.12** (DLP), **A.8.15** (logs), **A.8.16** (monitoramento), **A.8.23** (filtragem
> web). O **A.8.8** (vulnerabilidades) está `In Progress` pela mesma razão (evidência parcial).

## 2. O que a consultoria entregou

- **Governança:** DPO terceirizado (Bekaa Tecnologia Ltda, resp. técnico Ricardo Esper; auditoria 9.2 por parte independente); Ricardo Esper como consultor apenas; função de segurança atribuída ao cargo do CIO
  (Humberto). Ato de nomeação e Contrato de DPO **prontos para assinatura**.
- **Normas:** migração do SGPI para 27701:2025; SoA e SGPI-SoA reconciliados contra o nISO.
- **Adequação:** 24 controles de privacidade e 34 de segurança documentados/elevados com lastro; 15
  políticas/procedimentos de segurança redigidos; correções de aplicabilidade (nuvem, remoto, teste).
- **Integridade:** aprovações de CISO sem lastro **desaprovadas**; canal DSAR unificado; títulos e
  papéis padronizados. Campo **`owner` "CISO" → "CIO / Responsável de Segurança"** em **88 controles**
  (a TWYN não tem CISO) — aplicado por **API** após o nISO liberar a escrita do campo.
- **Vínculo de evidência (por API):** 8 evidências órfãs/mis-linkadas re-vinculadas aos controles
  (DPIA, DSAR, minimização, pentest, DevSecOps, incidentes, inventário); órfãos 35→28.
- **Encaminhamentos:** relatório de exports AWS (TI/DevOps, PDF); relatório do que restou de UI do nISO.

## 3. O que falta (quase tudo é do lado do cliente)

| # | Item | Responsável |
|---|---|---|
| 1 | **Exports do AWS `sa-east-1`** (Macie/DLP, CloudTrail, GuardDuty, Inspector, filtragem web) → fecha os **5 Missing** (A.8.11/12/15/16/23) + reforça A.8.8 — ver `RELATORIO-Tecnologia-Evidencias-AWS.md` | TI/DevOps (Marcelo/Nizar) |
| 2 | **Assinaturas:** Ato do DPO (CEO), anexar contrato DPO assinado + Cartão CNPJ da Bekaa | CEO / partes |
| 3 | **Auditoria interna 9.2 designada:** ness Processos e Tecnologia Ltda (auditora Monica Yoshida Barbosa) — instrumento `GOV-AUD-001`. **Pendente:** assinatura da declaração de imparcialidade + anexo das credenciais | ness / Direção TWYN |
| 4 | **Executar a auditoria interna 9.2** (27001+27701) contra evidência; tratar não conformidades (10.2) | ness (Monica) / Direção |

> **Nota:** a "sessão de UI do nISO" que antes constava aqui **deixou de ser necessária** — re-vínculo de
> evidência, status e `owner` já são executáveis por **API** (o nISO liberou a escrita de `owner`). Só
> restam higiene opcional do store e o julgamento de evidências `pending`, que não bloqueiam o Stage 1.

## 4. Caminho até o Stage 1

1. Cliente executa **(1)** exports do AWS → derruba os 5 Missing e reforça A.8.8.
2. **(2)** assinaturas → instrumentos de governança em vigor.
3. **(4)** auditoria interna 9.2 por parte independente → **parecer de prontidão** para o Stage 1.
4. Só então: **agendar o organismo certificador** (Stage 1 documental → Stage 2 em campo).

> A etapa **5** é o pré-requisito formal e o gargalo: sem a 9.2 independente, não há parecer de
> prontidão — e ela não pode ser feita pelo consultor de adequação.
