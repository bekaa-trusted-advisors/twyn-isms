# Solicitação de Evidências Técnicas (AWS) — Certificação ISO/IEC 27001 · TWYN Face ID Platform

| | |
|---|---|
| **Para** | Área de Tecnologia / DevOps (Marcelo Mascarenhas · Nizar Elouaer — CTO) |
| **De** | Consultoria de Adequação ISO 27001/27701 (ENG-2026-001) · Encarregado (DPO) |
| **Data** | 2026-08-25 |
| **Assunto** | Exportação de evidências do ambiente AWS para fechar 7 controles pendentes |
| **Ambiente** | AWS **`sa-east-1`** (São Paulo/Brasil) · EKS · RDS Aurora · S3 (buckets biométricos) · KMS |
| **Prioridade** | **Alta** — são os últimos controles técnicos que faltam para o Stage 1/2 |

---

## 1. Por que precisamos disto

Sete controles do Anexo A da ISO/IEC 27001:2022 **não têm evidência objetiva anexada** no sistema de
gestão (nISO). São controles **técnicos**, cuja prova só existe no ambiente AWS — por isso dependem de
vocês. Sem esses artefatos, os controles **não podem ser marcados como implementados** e travam a
auditoria de certificação.

> **Resumo:** cada item = print do console AWS **+** export do dado (JSON/CSV/PDF), nomeado por
> controle, com data e responsável. O **procedimento completo de entrega** está na **seção 3**.

---

## 2. O que precisamos, controle a controle

### 🔴 A.8.12 — Prevenção de Vazamento de Dados (DLP)
- **AWS Macie** habilitado nos **buckets de dados biométricos**: print da configuração + **export dos
  findings** (últimos 90 dias).
- **S3 Block Public Access** ativo (nível conta e bucket): print.
- Regras de **egress**/saída de dados (Security Groups / SCP) que impeçam exfiltração: export.

### 🔴 A.8.15 — Registros de Log
- **AWS CloudTrail**: print da configuração mostrando **trilha multi-região** e **Log File Validation
  = ON**; export da configuração (`aws cloudtrail describe-trails`, `get-trail-status`).
- **Retenção**: política de lifecycle do bucket de logs (S3/Glacier) — print/JSON.
- Se houver **SIEM** (Datadog/outro): print da ingestão de logs.

### 🔴 A.8.16 — Atividades de Monitoramento
- **AWS GuardDuty** habilitado: print + **export de findings** e do dashboard.
- **Alarmes do CloudWatch** para eventos de segurança (ex.: root login, alterações de IAM): print da
  lista de alarmes.

### 🔴 A.8.8 — Gestão de Vulnerabilidades Técnicas
- Ferramenta de varredura (**AWS Inspector** e/ou **ECR image scanning**): print da configuração.
- **Último relatório** de vulnerabilidades + **SLA de remediação** (prazo por severidade).

### 🔴 A.8.11 — Mascaramento de Dados
- Prova de **mascaramento/anonimização** de dados pessoais em ambientes de **não produção**
  (dev/homolog): print/consulta mostrando que **não há** biometria/PII real fora de produção.

### 🟡 A.8.23 — Filtragem Web  *(pode ser N/A)*
- Se houver **MDM/endpoint** com filtragem de conteúdo: política + print.
- **OU** confirmar formalmente que **não se aplica** (equipe 100% remota / BYOD sem gateway web
  corporativo) — nesse caso respondam "N/A" que registramos a justificativa.

### 🟠 A.8.29 — Testes de Segurança em Desenvolvimento
- Relatórios de **pentest / DAST / SAST / pipeline DevSecOps** (podem já existir — confirmar os mais
  recentes e a periodicidade).

---

## 3. Como enviar as evidências (procedimento e integridade)

Siga estes 5 passos — o que garante que a evidência seja **aceita pelo auditor** (íntegra e rastreável):

**1) Colete cada item em 2 formas:** o **print** do console AWS (mostrando o recurso e a data/hora) e,
quando aplicável, o **export bruto** via CLI. Exemplos:
```
aws cloudtrail describe-trails            > A.8.15_cloudtrail_trails.json
aws cloudtrail get-trail-status --name X  > A.8.15_cloudtrail_status.json
aws guardduty list-findings ...           > A.8.16_guardduty_findings.json
aws macie2 get-findings ...               > A.8.12_macie_findings.json
```

**2) Nomeie cada arquivo pelo controle:** `A.8.XX_descricao_AAAA-MM-DD.ext`
(ex.: `A.8.15_cloudtrail_status_2026-08-25.json`).

**3) Gere o hash (cadeia de custódia):** calcule o **SHA-256** de cada arquivo — é o que prova que o
arquivo **não foi alterado** depois da coleta.
- Linux/Mac: `sha256sum *`  ·  Windows PowerShell: `Get-FileHash * -Algorithm SHA256`

**4) Monte um índice** (planilha ou `README.csv`) com uma linha por evidência:
`controle · arquivo · SHA-256 · data da coleta · responsável · comando/fonte`.

**5) Entregue por canal controlado:**
- Preferencial: **subir direto no nISO** (store de evidências, vinculado ao controle) se a TI tiver
  acesso — o nISO registra o hash automaticamente.
- Alternativa: **pasta segura restrita** (Drive/S3 com acesso controlado) e avisar o DPO/consultoria,
  que anexa cada arquivo ao controle no nISO.
- **Não** usar e-mail/WhatsApp abertos; **não** incluir imagens/vetores biométricos ou qualquer PII de
  titular — apenas **configurações, políticas e relatórios técnicos**.

> Ao receber, a consultoria/DPO **vincula** cada evidência ao controle no nISO e **confirma** de volta,
> controle a controle. Só então o controle sai de `Missing`.

## 4. Reforço (desejável, não bloqueante)
- **A.8.11 / A.8.16 / A.8.8:** onde já houver evidência antiga no nISO, enviar a **versão atual** para
  substituir.

## 5. Próximos passos
1. Vocês reúnem os artefatos acima (prints + exports) conforme a seção 3.
2. A consultoria/DPO **anexa** cada evidência ao controle correspondente no nISO.
3. Os 7 controles passam de `Missing` para implementados → readiness recalculado.

> **Observação:** este relatório **não pede dado pessoal de titular** — apenas **configurações,
> políticas e relatórios técnicos** do ambiente. Não incluir imagens/vetores biométricos nos exports.
