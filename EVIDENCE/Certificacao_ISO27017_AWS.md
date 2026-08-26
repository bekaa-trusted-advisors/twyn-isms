# Relatório de Validação de Certificação de Segurança em Nuvem (ISO/IEC 27017) — AWS

> **Referência Normativa:** ABNT NBR ISO/IEC 27002:2022 (Diretrizes gerais de controles) / ISO/IEC 27017:2015 (Controles de segurança da informação específicos para serviços em nuvem)  
> **Status:** `VALIDADO E CONFORME`

Este documento registra a validação da certificação de controles de segurança da informação em nuvem da **Amazon Web Services (AWS)**, efetuada pela equipe de governança da Twyn a partir do certificado oficial fornecido pelo provedor.

---

## 📄 1. Metadados do Certificado

*   **Norma de Referência:** ISO/IEC 27017:2015 (Segurança da Informação para Provedores e Clientes de Serviços em Nuvem).
*   **Número do Certificado:** `2015-015` (Ciclo integrado ao certificado de Segurança ISO/IEC 27001:2022 nº `2013-009`).
*   **Organismo Certificador:** **EY CertifyPoint B.V.** (Organismo de certificação independente credenciado, Amsterdam, Holanda).
*   **Diretor Responsável:** Jatin Sehgal.
*   **Data de Emissão Atual:** 25 de novembro de 2025.
*   **Data de Reemissão técnica:** 20 de maio de 2026.
*   **Data de Expiração do Certificado:** **30 de novembro de 2028**.

---

## 🌍 2. Escopo e Cobertura Geográfica

O escopo do sistema de gestão certificado abrange a infraestrutura física, sistemas de controle, recursos humanos e processos operacionais de suporte de todos os datacenters e serviços de nuvem da AWS, incluindo expressamente:

*   **Localizações de Produção Utilizadas pela Twyn:**
    *   **Estados Unidos:** Região US East (Northern Virginia) (`us-east-1`).
    *   **Brasil:** Região South America (São Paulo) (`sa-east-1`).
*   **Manual de Gestão Auditado:** *AWS Integrated Information Management System (IIMS) Manual*, versão **2026.04**, datado de **18 de maio de 2026**.

---

## 🔒 3. Controles Específicos de Segurança em Nuvem (ISO 27017)

A certificação ISO 27017 auditada pela EY CertifyPoint garante que a AWS atende de forma operacional aos controles específicos de computação em nuvem, incluindo:

1.  **Segregação lógica e física de ambientes:** Garantias de virtualização robusta impedindo acesso cruzado a hosts e dados (hypervisor isolado).
2.  **Segurança em repouso e trânsito:** Configuração transparente de mecanismos criptográficos (KMS) com chaves AES-256 e APIs baseadas em TLS com forward secrecy.
3.  **Controle de mudanças operacional:** Alinhamento estrito do SDLC com testes de homologação segregados, sem utilização de dados reais de produção.
4.  **Logging e Monitoramento de Rede:** Detecção de intrusão, proteção contra DDoS e logging inalterável com custódia no S3 protegida por MFA.

---

## 📈 4. Parecer do Consultor

O certificado da AWS está **ativo, válido e plenamente homologado**. O cumprimento das diretrizes de segurança em nuvem da ISO 27017 pelo provedor de nuvem Tier 1 valida as premissas de segurança lógica e mitigação de vulnerabilidades da Twyn Face ID Platform.

---

## 📅 Histórico de Revisão

*   **Elaborado por:** Ricardo Esper (Consultor SGSIP)
*   **Aprovado por:** Kacio Giuliano Lopes (CEO)
*   **Data de Homologação:** 2026-07-27
*   **Revisão:** Periódica conforme ciclo de supervisão anual da EY.
