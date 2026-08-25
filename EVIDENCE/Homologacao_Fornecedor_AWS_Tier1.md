# Relatório de Diligência e Homologação de Fornecedor Crítico (Tier 1) — AWS

> **Controle ISO 27001:2022:** A.5.21 (Gestão de Segurança na Cadeia de Suprimentos de TIC) & A.5.22 (Monitoramento de Serviços de Fornecedores)  
> **Controle ISO 27701:2019:** Cláusula 7.2.4 (Diligência com operadores/fornecedores)  
> **Status do Fornecedor:** `HOMOLOGADO (Tier 1 - Risco Crítico)`

Este documento registra a análise técnica de segurança e privacidade do fornecedor **Amazon Web Services (AWS)** executada pela equipe de governança da Twyn, fundamentada no relatório de auditoria independente **System and Organization Controls (SOC 3) Report** correspondente ao período de **1 de abril de 2025 a 31 de março de 2026**, emitido pela **Ernst & Young LLP (EY)** em **29 de maio de 2026**.

---

## 🖥️ 1. Identificação do Fornecedor e Escopo dos Serviços

*   **Fornecedor:** Amazon Web Services, Inc. (AWS)
*   **Criticidade:** **Tier 1 (Crítico):** Hospeda 100% da infraestrutura de produção e da aplicação **Face ID API** da Twyn.
*   **Região de Produção (dados pessoais):** **South America (São Paulo) (`sa-east-1`)** — os vetores biométricos e a base de produção residem no **Brasil**. _(Correção ENG-2026-001: registro anterior citava também `us-east-1` (EUA); os dados pessoais permanecem em território nacional — sem transferência internacional.)_
*   **Serviços AWS no Escopo da Diligência:**
    *   **Amazon EKS (Elastic Kubernetes Service):** Processamento e execução da API.
    *   **Amazon RDS (Relational Database Service):** Armazenamento de metadados e vetores biométricos criptografados.
    *   **Amazon S3 (Simple Storage Service):** Armazenamento de logs operacionais históricos.
    *   **AWS Key Management Service (KMS):** Gestão e custódia de chaves criptográficas AES-256.
    *   **Amazon VPC (Virtual Private Cloud):** Isolamento lógico de rede.

---

## 🛡️ 2. Avaliação dos Controles de Segurança (SOC 2 Type II & SOC 3)

A auditoria independente conduzida pela **Ernst & Young LLP (EY)** atestou eficácia operacional sem desvios (**No deviations noted**) nos seguintes controles críticos da infraestrutura da AWS:

### A. Segurança Lógica e Controle de Acessos (A.5.15 / A.5.18 / A.6.5)
*   **Controle de Acessos Lógicos (AWSCA-2.3):** EY validou os processos de revisão trimestral de privilégios de acesso administrativo e re-aprovação formal; acessos sem justificativa são revogados automaticamente. 
*   **Revogação de Colaboradores (AWSCA-2.4):** Acesso de funcionários demitidos/desligados aos sistemas corporativos e ambientes de infraestrutura é revogado e desativado em no máximo **24 horas** no Windows AD e Unix LDAP.
*   **Política de Senhas (AWSCA-2.5):** Complexidade de senha (mínimo 8 caracteres, rotação, etc.), bloqueio automático após 6 tentativas e bloqueio de reuso das últimas 15 senhas.
*   **Isolamento Multi-tenant (AWSCA-3.10 / AWSCA-3.12):** O hypervisor AWS impede ativamente packet sniffing entre instâncias e isola a comunicação de rede de VMs rodando na mesma máquina física.

### B. Gestão e Custódia de Chaves Criptográficas (A.8.24 / A.5.17)
*   **Acesso Restrito a Chaves (AWSCA-4.5):** O KMS restringe o acesso lógico de funcionários da AWS a qualquer chave criptográfica hospedada em HSMs, exigindo aprovação multipartidária (quórum) para qualquer alteração técnica.
*   **Criptografia AES-256 (AWSCA-4.7):** Os algoritmos de criptografia de dados operam sob o padrão seguro AES de 256 bits, com endpoints acessíveis apenas via TLS suportando *forward secrecy* (AWSCA-4.9).
*   **Logs Inalteráveis (AWSCA-4.8):** Cada chamada às APIs do KMS é logged no AWS CloudTrail de forma auditável e transparente para o cliente.

### C. Segurança Física e Proteção Ambiental de Datacenters (A.7)
*   **Acesso Físico Restrito (AWSCA-5.1 a AWSCA-5.3):** Entrada permitida apenas a funcionários autorizados; revisão trimestral de crachás; revogação de acessos físicos em 24h para desligados.
*   **Segurança Perimetral e CFTV (AWSCA-5.4 a AWSCA-5.6):** Presença de alarmes perimetrais físicos, sensores de intrusão, leitoras biométricas/badge + PIN e gravação contínua de CFTV retida por no mínimo 90 dias.
*   **Sanitização de Mídias Descartadas (AWSCA-5.13):** Trituração e destruição física de mídias de armazenamento permanentes (HDD/SSD/NVMe) sob o padrão **NIST SP 800-88** verificada por dois operadores independentes.
*   **Prevenção de Incêndios e Energia (AWSCA-5.7 a AWSCA-5.10):** Datacenters protegidos por sistemas de detecção de fumaça MASD, sprinklers a gás e geradores de energia redundantes com baterias UPS (BBU) continuamente monitoradas.

### D. Gestão de Mudanças e SDLC (A.8.25 / A.8.19)
*   **Ambientes Segregados (AWSCA-6.4):** Separação lógica total entre os ambientes de desenvolvimento/teste e produção.
*   **Peer Review e Testes (AWSCA-6.5 / AWSCA-6.7):** Modificações em código passam por revisão por pares e testes automatizados. É proibido o uso de dados reais de clientes (produção) em ambientes de testes e homologação.

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

*   **Elaborado por:** Ricardo Esper (Consultor SGSIP)
*   **Aprovado por:** Kacio Lopes (CEO)
*   **Data de Homologação:** 2026-07-27
*   **Próxima Revisão:** Julho de 2027 (ou mediante publicação de novo relatório SOC 3 anual)
