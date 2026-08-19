# Checklist de Export de Evidência — Ambiente AWS

**Para:** Marcelo Mascarenhas (DevOps Lead / T4ISB) — infra AWS `us-east-1`
**De:** Consultoria Aegis — ENG-2026-001
**Objetivo:** exportar evidência objetiva para os controles críticos que **não** têm artefato no nISO.
Suba cada export no controle indicado (nISO, projeto `mr9c1qugo16zic2eko`) ou envie ao DPO para anexar.

> Formato aceito: JSON/PDF/PNG. Cada export deve ser **datado, atribuível e verificável** (não editar à
> mão). O que prova conformidade é a **configuração real**, não a política.

## Prioridade ALTA (fecham achado crítico)

| # | Controle | O que exportar | Como | O que prova |
|---|---|---|---|---|
| 1 | **A.8.12 — DLP / Prevenção de Vazamento** | (a) Config e **findings do AWS Macie** sobre os buckets biométricos; (b) **S3 Block Public Access** (conta + buckets); (c) regras de egress/DLP se houver | Console/CLI: `aws macie2 get-findings`, `aws s3control get-public-access-block` | Proteção contra vazamento de dado sensível |
| 2 | **A.8.15 — Registros de Log** | (a) Config do **CloudTrail** (trails multi-região, *log file validation* ON); (b) **retenção** de logs (lifecycle S3/R2); (c) CloudWatch Logs/SIEM se houver | `aws cloudtrail describe-trails`, `get-trail-status`, `aws s3api get-bucket-lifecycle-configuration` | Registro e retenção de eventos |
| 3 | **A.8.23 — Filtragem Web** | Política de filtragem web via **MDM/endpoint** (Jamf/Intune/antivírus) **— OU** decisão formal de **`N/A`** se não há endpoints corporativos gerenciados (equipe 100% remota, BYOD) | Export do console MDM, ou memorando de exclusão assinado | Filtragem web, ou exclusão justificada |

## Prioridade MÉDIA (reforço — evidência existente é fraca)

| # | Controle | O que exportar | O que prova |
|---|---|---|---|
| 4 | **A.8.11 — Mascaramento** | Consulta/config demonstrando **dado mascarado em não-produção** (ex.: dump anonimizado, regra de masking no RDS/ETL) | Masking real (além da diretriz) |
| 5 | **A.8.16 — Monitoramento** | **Findings/dashboard do GuardDuty** + lista de **alarmes CloudWatch** ativos | Monitoramento ativo (além da política) |
| 6 | **A.8.8 — Vulnerabilidades (reforço)** | Config do **scanner** (AWS Inspector/equivalente) + **SLA de remediação** e último ciclo | Gestão contínua de vulnerabilidades |

## Observações

- **A.8.22 Segregação de Redes:** já há `AWS-VPC-Architecture.png` no store; se possível, complementar com
  export de **Security Groups / NACLs** por VPC. (A reclassificação p/ Aplicável é ação do DPO no UI.)
- Não editar exports manualmente — o valor probatório vem de serem gerados pela própria AWS.

---
**Entrega:** ao concluir 1–3, os 3 críticos remanescentes são fechados; 4–6 elevam a maturidade dos
controles já vinculados. Conformidade final é decidida na auditoria interna (9.2) independente.
