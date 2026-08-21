# Relatório de Diligência de Governança e Integridade Financeira (SOC 1) — AWS

> **Controle ISO 27001:2022:** A.5.22 (Monitoramento, análise crítica e gestão de mudanças de serviços de fornecedores) & A.5.36 (Conformidade com políticas e normas)  
> **Status:** `APROVADO E HOMOLOGADO`

Este documento registra a análise técnica de governança operacional e integridade contábil/financeira do fornecedor **Amazon Web Services (AWS)** conduzida pela Twyn. A análise fundamenta-se no relatório de auditoria independente **System and Organization Controls 1 (SOC 1) Type 2 Report** para o período de **1 de abril de 2025 a 31 de março de 2026**, emitido pela **Ernst & Young LLP (EY)** em **29 de maio de 2026**.

---

## 📈 1. Escopo de Controle Interno e Faturamento (ICFR)

O relatório SOC 1 Type II atesta formalmente a eficácia do sistema de controle interno da AWS relevante para o faturamento e relato financeiro das organizações usuárias (Twyn). As seguintes dimensões foram avaliadas pelo auditor (EY) sem qualquer exceção ou desvio (**No deviations noted**):

### A. Integridade de Processamento de Dados (Control Objective 6)
*   **Detecção de Corrupção em Trânsito (AWSCA-7.1):** AWS executa validações de integridade por meio de hashes MD5 e SHA-256 nas requisições REST da API de armazenamento do Amazon S3, inviabilizando deploy ou tráfego de dados corrompidos.
*   **Integridade dos Dados em Repouso (AWSCA-7.2):** S3 executa continuamente verificações automáticas de integridade contra checksums nos objetos em disco. Em caso de falha física, reconstrói a redundância de forma autônoma (AWSCA-7.3).
*   **Redundância e Replicação (AWSCA-7.4 a AWSCA-7.6):** Armazenamento em S3 distribuído em múltiplas instalações com isolamento de falhas. Bancos de dados Amazon RDS executam backups automáticos programados e restaurações pontuais (*Point-in-Time Recovery - PITR*).

### B. Gestão de Capacidade e Performance (Control Objective 8)
*   **Modelagem de Capacidade (AWSCA-10.4):** AWS realiza revisões formais de capacidade de infraestrutura em nível regional e de Edge Locations em cadência mensal (e semanal para serviços críticos), assegurando que o processamento e a escalabilidade dos servidores EKS e RDS da Twyn atendam às demandas computacionais.
*   **Redundância e Resiliência (Control Objective 6):** Replicação de componentes vitais em Zonas de Disponibilidade (AZs) independentes e geograficamente separadas, com fontes de energia e climatização redundantes (N+1).

### C. Tratamento de Logs e Incidentes (Control Objective 7)
*   **Notificação de Incidentes (AWSCA-8.1):** Acionamento automatizado de alarmes por limiares críticos monitorados por donos de serviços na AWS, com escalonamento por pagers operando 24x7.
*   **Auditoria de Logs (AWSCA-8.3):** Logging centralizado de atividades administrativas do sistema. O acesso a logs de agregação requer autenticação multi-fator (MFA) e ferramentas de permissão bloqueiam qualquer exclusão ou modificação por funcionários da AWS.

---

## ⚖️ 2. Conclusão da Diligência

A homologação da AWS sob o relatório SOC 1 assegura que:

1.  **Faturabilidade e SLAs:** Os controles operacionais que suportam o cálculo de faturamento e consumo dos datacenters AWS são íntegros e auditados, minimizando riscos de interrupção contratual por divergência contábil.
2.  **Mitigação de Impacto Contábil:** A Twyn valida a integridade financeira de sua cadeia de suprimentos de TIC, confirmando a robustez operacional do fornecedor crítico Tier 1.

---

## 📅 Histórico de Homologação

*   **Elaborado por:** Ricardo Esper (Consultor SGSIP)
*   **Aprovado por:** Kacio Lopes (CEO)
*   **Data de Homologação:** 2026-07-27
*   **Revisão:** Anual (mediante novos relatórios SOC 1)
