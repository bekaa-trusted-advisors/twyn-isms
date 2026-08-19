# Dossiê de Coleta de Evidência — 17 achados críticos ("assinatura sem lastro")

| Campo | Valor |
|---|---|
| Engajamento | ENG-2026-001 |
| Data | 2026-08-19 |
| Origem | readiness nISO — 17 críticos `doc_inconsistente / assinatura sem lastro` |
| Método | Mapear evidência **existente** (repo/nISO) → **vincular no UI**; e especificar o que **falta exportar** do ambiente. **Nada fabricado.** |

> **Limite de API:** o papel `consultant` **não re-vincula evidência** por HTTP (`PUT /evidence/{id}` → 404).
> Portanto os "vincular" abaixo são **ações no UI do nISO** (ou upload). Os "exportar" exigem acesso ao
> ambiente AWS que o consultor não possui. Avaliação de conformidade final: auditoria 9.2 independente.

---

## Parte 1 — 9 controles `Not Applicable` (A.7.x físicos): **sem evidência de implementação**

A.7.1, A.7.2, A.7.3, A.7.4, A.7.5, A.7.6, A.7.8, A.7.11, A.7.12 são **N/A** (equipe 100% remota, infra
100% AWS) e **já têm justificativa** (campo `description`). O readiness os marca "sem evidência", mas
**N/A não requer evidência de implementação** — o lastro é a justificativa. → **Ação:** aceitar/`fechar`
o achado como falso-positivo de N/A (documentar a justificativa como o lastro). Nenhuma coleta técnica.

## Parte 2 — 7 controles **aplicáveis** (precisam de evidência real)

### ✅ Já satisfazíveis por vínculo (evidência existe no store — vincular no UI)

| Controle | Evidência existente (nISO) | Ação |
|---|---|---|
| **A.8.29 Testes de Segurança (Dev/Aceitação)** | `Relatorio_Pentest_Vulnerabilidades_Fase32.txt` (órfã, id `b63d7205…`), `dast_scan_results.pdf`, `sast_pipeline_report.pdf`, `Engenharia_Seguranca_DevSecOps_Fase18.txt` (órfã, id `3e5885a6…`) | **Vincular** a `ctrl-a829`. Evidência forte já existe. |
| **A.8.8 Gestão de Vulnerabilidades** | `Relatorio_Pentest_Vulnerabilidades_Fase32.txt` (órfã), `dast_scan_results.pdf`, `POL-THR-001 GuardDuty/MISP` | **Vincular** o pentest a `ctrl-a88`. Complementar com SLA de remediação. |
| **A.8.16 Atividades de Monitoramento** | `POL-THR-001 GuardDuty/MISP`, `SGSI-METRICS-001 Relatório de Monitoramento` | **Vincular** a `ctrl-a816`. Reforçar com export de findings do GuardDuty. |
| **A.8.11 Mascaramento de Dados** | `Diretrizes_Anonimizacao_Privacidade_Fase23.txt` (órfã, id `84c7f9c5…`) | **Vincular** a `ctrl-a811` — porém é *diretriz*, não prova de masking em não-prod (ver abaixo). |

### ⚠ Precisam de evidência fresca do ambiente (exportar — só o cliente/ops)

| Controle | O que falta (evidência objetiva a exportar) |
|---|---|
| **A.8.12 Prevenção de Vazamento (DLP)** | **Nenhum candidato no store.** Exportar: config AWS Macie (ou equivalente), S3 Block Public Access, regras de egress/DLP. |
| **A.8.15 Registros de Log** | **Sem artefato de log.** Exportar: config do AWS CloudTrail (trails multi-região), retenção de logs (S3/R2), e SIEM se houver. |
| **A.8.23 Filtragem Web** | **Nenhum candidato.** Exportar: config de filtragem web via MDM/endpoint — **ou** decidir `N/A` se não há endpoints corporativos gerenciados (equipe remota). **Decisão de escopo do cliente.** |
| **A.8.11 (reforço)** | Além da diretriz, exportar prova de **masking real** em ambientes não-produtivos (config/consulta demonstrando dado mascarado). |
| **A.8.16 (reforço)** | Export de **findings/dashboards** do GuardDuty + alarmes CloudWatch (a política sozinha não basta). |

---

## Parte 3 — Achados adjacentes descobertos na coleta (governança)

- **A.8.22 Segregação de Redes está `Not Applicable` — incorreto.** Existe `AWS-VPC-Architecture.png`
  (vinculada a A.8.20) evidenciando segregação por VPC/SG. → **Reclassificar A.8.22 para Aplicável** e
  vincular a arquitetura VPC. (Decisão de aplicabilidade — sua.)
- **Evidências órfãs valiosas a religar:** `SOC 1/2/3 Reports`, `dpaAWS.pdf`, `scc_AWS_Service_Terms…pdf`
  (control_id nulo) → candidatas a A.5.19/A.5.22 (fornecedor AWS), A.5.23 (nuvem), A.5.34 (transferência).

---

## Resumo acionável

| Grupo | Qtde | Próxima ação | Quem |
|---|---:|---|---|
| N/A físicos (falso-positivo) | 9 | Fechar achado via justificativa | Consultor/DPO (UI) |
| Aplicáveis satisfazíveis por vínculo | 3–4 | Vincular evidência existente no UI | Cliente (UI nISO) |
| Aplicáveis que exigem export | 3 | Exportar do AWS (Macie/CloudTrail/WebFilter) | Ops/DevOps (Marcelo) |
| Aplicabilidade a rever | 1 (A.8.22) | Reclassificar Aplicável | CISO |

> Assim que a evidência for vinculada/exportada, a **conformidade** de cada controle é decidida na
> auditoria 9.2 **independente** — não pelo consultor que a coletou.
