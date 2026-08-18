# Matriz de Gestão de Riscos — TWYN Face ID Platform

> **Referência Normativa:** ISO/IEC 27005:2022 / Cláusula 6.1 do SGSI (ISO 27001)  
> **Metodologia:** Análise de Impacto (1-5) x Probabilidade (1-5) conforme critérios de apetite de risco da Twyn.

Este registro contém a listagem ativa de riscos de segurança e privacidade identificados no escopo da plataforma **Face ID API** e da infraestrutura AWS, juntamente com os respectivos planos de tratamento mitigados.

---

## Matriz de Riscos Mapeados

| ID Risco | Ativo Associado | Ameaça / Cenário | Vulnerabilidade | Criticidade | Status | Plano de Tratamento / Mitigação | Proprietário |
|---|---|---|---|---|---|---|---|
| **risk-twyn-01** | Face ID API | Acesso não autorizado | MFA não obrigatório em todos os endpoints | `Low` | `Mitigated` | Mitigado via conformidade técnica do controle A.5.15 Controle de Acesso. | Security Team |
| **risk-twyn-02** | AWS RDS | Vazamento de Dados Biométricos | Criptografia em repouso não validada | `Low` | `Mitigated` | Mitigado via conformidade técnica do controle A.8.24 Uso de Criptografia. | Security Team |
| **risk-twyn-04** | AWS IAM Credentials | Vazamento de Chaves Privadas | Uso de .env files legados | `Low` | `Open` | ⚠ ENG-2026-001: tratamento apoiado no controle **A.5.17**, que consta `Missing` no SoA. Reaberto até implementação/evidência do controle. | Security Team |
| **risk-twyn-06** | S3 Biometric Buckets | Biometric data breach (S3 misconfig) | Public access possible, lack of encryption | `Low` | `Mitigated` | Mitigado via conformidade técnica do controle A.8.24 Uso de Criptografia. | Security Team |
| **risk-twyn-07** | AWS Root Account | Unauthorized root access | Root used for daily ops, key stored insecurely | `Low` | `Mitigated` | Mitigado via conformidade técnica do controle A.5.15 Controle de Acesso. | Security Team |
| **risk-twyn-08** | EKS Clusters | Ransomware attack | Cluster monitoring gaps, unpatched nodes | `Low` | `Mitigated` | Mitigado via conformidade técnica do controle A.8.16 Atividades de Monitoramento. | Security Team |
| **risk-twyn-10** | AWS Account | Lack of Threat Detection | No GuardDuty active | `Low` | `Mitigated` | Mitigado via conformidade técnica do controle A.5.7 Inteligência sobre Ameaças. | Security Team |
| **risk-twyn-03** | Bucket R2 | Exposição acidental de logs | Políticas de bucket permissivas | `Low` | `Open` | ⚠ ENG-2026-001: tratamento apoiado no controle **A.8.12 (DLP)**, que consta `Missing` no SoA. Reaberto até implementação/evidência do controle. | Security Team |
| **risk-twyn-09** | IAM Policies | IAM Over-permissioning (Insider) | Many users with AdministratorAccess | `Low` | `Mitigated` | Mitigado via conformidade técnica do controle A.5.18 Direitos de Acesso. | Security Team |
| **risk-twyn-11** | Enquadramento Jurídico de Biometria | Questionamento da base legal do tratamento biométrico sensível por reguladores ou parceiros B2B | Classificação incorreta da TWYN como mera operadora ou falta de amparo jurídico formal no Art. 11, II, 'g' da LGPD | `Low` | `Mitigated` | Mitigado formalmente através do Parecer Jurídico Especializado Machado Meyer Ref 116764899 (enquadramento no Art. 11, II, 'g' da LGPD para Prevenção à Fraude), alinhado ao Termo de Co-Controladoria Independente e DPA B2B (POL-LEG-002). | Ricardo Esper (DPO) |
| **risk-twyn-12** | Algoritmo de Vetorização Biométrica | Reversibilidade teórica do vetor numérico ou ataques de representação (Presentation Attacks / Deepfakes) | Tentativas de reconstituição fotográfica ou injeção de amostras biométricas sintéticas | `Low` | `Mitigated` | Adoção de modelos de extração de recursos unidirecionais matematicamente irreversíveis (sem reconstituição fotográfica); Liveness Detection ativo na API; expurgo instantâneo em memória RAM (0s) de fotos brutas; criptografia AES-256 no RDS. | Nizar Elouaer (CTO) |
| **risk-twyn-05** | AWS Config | Não Conformidade com AWS FTR | AWS Config não plenamente operacional | `Low` | `Open` | ⚠ ENG-2026-001: tratamento apoiado no controle **A.8.9 Gestão de Configuração**, que consta `Missing` no SoA. Reaberto até implementação/evidência do controle. | Security Team |

---

## Análise de Severidade

*   **Critérios de Criticidade:**
    *   **Crítico (15-25):** Mitigação imediata mandatória; monitoramento contínuo em nível executivo.
    *   **Alto (9-14):** Ações de tratamento obrigatórias em até 30 dias.
    *   **Médio (4-8):** Controles operacionais preventivos em vigor.
    *   **Baixo (1-3):** Risco aceito operacionalmente pela diretoria.

Este registro é homologado e revisado semestralmente pelo DPO Ricardo Esper e validado tecnicamente pelo CTO Nizar Elouaer.
