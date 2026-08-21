# Tarefa — Vínculos e aplicabilidade no nISO (UI)

**Para:** Ricardo Esper (Consultor) — ou quem opera o nISO
**De:** Consultoria Aegis — ENG-2026-001
**Contexto:** os 17 achados críticos do readiness são "controle assinado sem evidência anexada". Boa
parte da evidência **já existe** no store do nISO, apenas **não está vinculada** ao controle. Estas
ações são no **UI do nISO** (a API do papel consultor não re-vincula evidência). Projeto: `mr9c1qugo16zic2eko`.

> Nenhuma dessas ações declara conformidade — apenas anexa evidência objetiva já existente. O julgamento
> de conformidade é da auditoria interna (9.2), por sessão independente.

## 1. Vincular evidência existente aos controles (órfãs → controle)

| Controle | Evidência (já no store) | id (se órfã) |
|---|---|---|
| **A.8.29** Testes de Segurança (Dev/Aceitação) | `Engenharia_Seguranca_DevSecOps_Fase18.txt` | `3e5885a6…` |
| **A.8.29** | `Relatorio_Pentest_Vulnerabilidades_Fase32.txt` (cópia/segundo vínculo) | `b63d7205…` |
| **A.8.29** | `dast_scan_results.pdf`, `sast_pipeline_report.pdf` (já vinculados a A.8.25/A.8.28 — anexar cópia) | — |
| **A.8.8** Gestão de Vulnerabilidades | `Relatorio_Pentest_Vulnerabilidades_Fase32.txt` | `b63d7205…` |
| **A.8.11** Mascaramento de Dados | `Diretrizes_Anonimizacao_Privacidade_Fase23.txt` (diretriz — reforçar com prova de masking, ver tarefa Ops) | `84c7f9c5…` |
| **A.8.16** Atividades de Monitoramento | `POL-THR-001 GuardDuty/MISP`, `SGSI-METRICS-001 Monitoramento` (reforçar com findings, ver Ops) | — |

> Obs.: cada evidência tem **um** `control_id`. Onde a mesma peça serve a dois controles (ex.: pentest →
> A.8.8 e A.8.29), duplicar a entrada/upload no segundo controle.

## 2. Reclassificar aplicabilidade

- **A.8.22 Segregação de Redes** está `Not Applicable` — **incorreto** para plataforma cloud. Existe
  `AWS-VPC-Architecture.png` (hoje em A.8.20) evidenciando segregação por VPC/Security Groups.
  → **Mudar A.8.22 para Aplicável** e vincular a arquitetura VPC.

## 3. Fechar os 9 N/A físicos (falso-positivo do readiness)

A.7.1, A.7.2, A.7.3, A.7.4, A.7.5, A.7.6, A.7.8, A.7.11, A.7.12 são **N/A** (equipe 100% remota, infra
AWS) e **já têm justificativa**. N/A não requer evidência de implementação. → Confirmar a justificativa
como o lastro; se o readiness exigir um anexo, subir o **modelo de responsabilidade compartilhada AWS**
como evidência de exclusão.

## 4. Religar evidências órfãs valiosas (higiene)

`SOC 1/2/3 Reports`, `dpaAWS.pdf`, `scc_AWS_Service_Terms…pdf` estão com `control_id` nulo →
vincular a A.5.19/A.5.22 (fornecedor AWS), A.5.23 (nuvem) e A.5.34 (transferência), conforme o caso.

---
**Resultado esperado:** os 17 críticos caem para ~3 (os que dependem de export do AWS — ver tarefa Ops),
e o readiness melhora materialmente.
