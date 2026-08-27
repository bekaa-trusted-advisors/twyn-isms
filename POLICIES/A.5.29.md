# POL-BCP-001: Política de Continuidade de Negócios (BCP) — TWYN Face ID Platform
**ISO/IEC 27001:2022 Controles A.5.29 (Segurança da informação durante interrupção) e A.5.30 (Prontidão de TIC para continuidade de negócios)**

---

**Controle de Documento**

| Campo | Valor |
|-------|-------|
| **Document ID** | POL-BCP-001 |
| **Version** | 1.0 (Oficial) |
| **Autor** | Ricardo Esper (Consultor) |
| **Aprovador** | Kacio Giuliano Lopes (CEO) |
| **Data de Emissão** | 16/07/2026 |
| **Status** | `Aprovado` |

---

## 1. Objetivo

Garantir a resiliência operacional da Face ID Platform, estabelecendo as diretrizes para a prontidão dos serviços de tecnologia (TIC) em caso de interrupções ou desastres estruturais.

---

## 2. Metas de Continuidade (RTO e RPO)

As seguintes metas de recuperação ficam estabelecidas para a infraestrutura de produção AWS da API Face ID:
*   **RTO (Recovery Time Objective):** Tempo máximo tolerado de indisponibilidade da API fixado em **2 horas**.
*   **RPO (Recovery Point Objective):** Perda máxima tolerada de dados fixada em **24 horas** (baseada na frequência diária de backups).

---

## 3. Prontidão e Redundância de TIC (A.5.30)

1.  **Redundância Multi-AZ:** O cluster EKS e os microsserviços auxiliares da API devem operar de forma redundante distribuídos em no mínimo 3 Zonas de Disponibilidade (AZs) da AWS.
2.  **Replicação do Banco de Dados:** O banco RDS Aurora PostgreSQL deve operar em modo Multi-AZ com réplica síncrona habilitada para failover automático em menos de 60 segundos.
3.  **Backups Criptografados:** O AWS Backup automatizado deve realizar backups diários do RDS com retenção de 30 dias, criptografados com chave AWS KMS dedicada (conforme `POL-TX-001`).

---

## 4. Testes de Restauração (Disaster Recovery - DR)

1.  **Testes Semestrais:** O DevOps Marcelo Mascarenhas deve realizar simulações formais de restauração (restore tests) do banco de dados e da API em ambiente isolado de Staging a cada **6 meses**.
2.  **Registro de Evidência:** Cada teste de restore executado deve gerar uma ata de teste detalhando: data de início, tempo total de restabelecimento (RTO obtido), integridade dos dados validados e a assinatura técnica do responsável.

---

## 5. Revisão e Aprovação

Esta política é aprovada pela Diretoria Executiva da TWYN e revisada anualmente.

**Kacio Giuliano Lopes**  
CEO / Patrocinador Executivo  
TWYN T4ISB DO BRASIL TECNOLOGIA E PARTICIPACOES LTDA (CNPJ: 31.122.819/0001-55)
*Assinado eletronicamente via TWYN GRC Portal em 21/07/2026 18:00 BRT (IP: 189.122.34.55, Hash: 51398117157b023b821073858bc310be)*
