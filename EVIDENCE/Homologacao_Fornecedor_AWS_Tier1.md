# Relatório de Diligência e Homologação de Fornecedor Crítico (Tier 1) — AWS

> **Controle ISO 27001:2022:** A.5.21 (Gestão de Segurança na Cadeia de Suprimentos de TIC) & A.5.22 (Monitoramento de Serviços de Fornecedores)  
> **Controle ISO 27701:2019:** Cláusula 7.2.4 (Diligência com operadores/fornecedores)  
> **Status do Fornecedor:** `HOMOLOGADO (Tier 1 - Risco Crítico)`

Este documento registra a análise técnica de segurança e privacidade do fornecedor **Amazon Web Services (AWS)** executada pela equipe de governança da Twyn, fundamentada no relatório de auditoria independente **System and Organization Controls (SOC 3) Report** correspondente ao período de **1 de abril de 2025 a 31 de março de 2026**, emitido pela **Ernst & Young LLP (EY)** em **29 de maio de 2026**.

---

## 🖥️ 1. Identificação do Fornecedor e Escopo dos Serviços

*   **Fornecedor:** Amazon Web Services, Inc. (AWS)
*   **Criticidade:** **Tier 1 (Crítico):** Hospeda 100% da infraestrutura de produção e da aplicação **Face ID API** da Twyn.
*   **Regiões Utilizadas:** **US East (Northern Virginia) (us-east-1)** e **South America (São Paulo) (sa-east-1)**.
*   **Serviços AWS no Escopo da Diligência:**
    *   **Amazon EKS (Elastic Kubernetes Service):** Processamento e execução da API.
    *   **Amazon RDS (Relational Database Service):** Armazenamento de metadados e vetores biométricos criptografados.
    *   **Amazon S3 (Simple Storage Service):** Armazenamento de logs operacionais históricos.
    *   **AWS Key Management Service (KMS):** Gestão e custódia de chaves criptográficas AES-256.
    *   **Amazon VPC (Virtual Private Cloud):** Isolamento lógico de rede.

---

## 🛡️ 2. Avaliação dos Controles de Segurança (SOC 3 / ISO 27001)

### A. Segurança Lógica e Isolamento (Multi-tenancy)
*   **Constatação do Auditor (EY):** A AWS implementa mecanismos eficazes de hypervisor para garantir o isolamento total de computação, armazenamento e recursos de rede. Clientes não conseguem acessar instâncias físicas ou dados pertencentes a outros tenants.
*   **Mitigação de Rede (VPC):** O tráfego de entrada é configurado como *deny-all* por padrão através de Security Groups e Network ACLs.

### B. Gestão e Custódia de Chaves (Criptografia)
*   **Segurança no KMS:** O AWS KMS utiliza Módulos de Segurança de Hardware (HSMs) customizados e certificados. As chaves criptográficas em repouso nunca são expostas em texto puro fora desses HSMs.
*   **Controle de Acesso:** O acesso administrativo é restrito por políticas IAM rígidas e todas as requisições de chaveamento geram logs auditáveis inalteráveis via AWS CloudTrail.

### C. Sanitização e Descarte de Mídia (NIST SP 800-88)
*   **Processo de Decommissioning:** Dispositivos de armazenamento que chegam ao fim do ciclo de vida útil ou são substituídos passam por processos de sanitização física e trituração lógica seguindo o padrão **NIST SP 800-88** (*Guidelines for Media Sanitization*), inviabilizando qualquer recuperação de dados históricos.

---

## 👁️‍🗨️ 3. Avaliação dos Controles de Privacidade (SOC 3 / ISO 27701)

### A. Proteção ao Conteúdo do Cliente (*Customer Content*)
*   **Propriedade dos Dados:** O relatório confirma que a AWS assegura a propriedade exclusiva do cliente sobre os dados armazenados (*Customer Content*). A AWS não utiliza dados de clientes para propósitos secundários, desenvolvimento ou treinamento.
*   **Não Divulgação Governamental:** AWS possui políticas formais de rejeitar requisições governamentais de dados de clientes, a menos que amparadas por ordens judiciais juridicamente válidas e vinculantes.

### B. Gestão de Subprocessadores de TIC
*   **Controle de Terceiros:** A AWS mantém uma lista pública e atualizada de sub-processadores autorizados e impõe obrigações contratuais equivalentes às chaves de privacidade do contrato principal do cliente.

---

## 📈 4. Veredito e Postura de Conformidade

Com base na opinião independente emitida pelos auditores da **Ernst & Young LLP (EY)**, que atestou a eficácia operacional de todos os critérios de confiança (Segurança, Disponibilidade, Confidencialidade e Privacidade) da AWS no período auditado:

1.  **Postura Geral:** **Excelente.** O relatório não apresentou nenhuma ressalva, exceção ou desvio em controles críticos de infraestrutura ou proteção de dados.
2.  **Mitigação de Riscos de Terceiros:** O modelo de **Responsabilidade Compartilhada** é plenamente atendido pela Twyn ao parametrizar criptografia AES-256 gerenciada por KMS, restrições VPC rígidas e expurgo em memória RAM (0s).
3.  **Homologação:** O fornecedor está **APROVADO E HOMOLOGADO** para continuar operando como a nuvem da Twyn Face ID Platform.

---

## 📅 Histórico de Revisão

*   **Elaborado por:** Ricardo Esper (DPO / Consultor SGSIP)
*   **Aprovado por:** Kacio Lopes (CEO)
*   **Data de Homologação:** 2026-07-27
*   **Próxima Revisão:** Julho de 2027 (ou mediante publicação de novo relatório SOC 3 anual)
