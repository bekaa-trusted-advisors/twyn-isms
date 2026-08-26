# POL-CMP-001: Política de Gestão de Mudanças — TWYN Face ID Platform
**ISO/IEC 27001:2022 Controle A.8.32 (Gestão de mudanças)**

---

**Controle de Documento**

| Campo | Valor |
|-------|-------|
| **Document ID** | POL-CMP-001 |
| **Version** | 1.0 (Oficial) |
| **Autor** | Ricardo Esper (Consultor) |
| **Aprovador** | Kacio Giuliano Lopes (CEO) |
| **Data de Emissão** | 16/07/2026 |
| **Status** | Aprovado |

---

## 1. Objetivo

Garantir que todas as alterações no código-fonte da API, bancos de dados e infraestrutura em nuvem AWS da TWYN sejam planejadas, autorizadas, testadas e implementadas de forma controlada e segura, mitigando indisponibilidades operacionais.

---

## 2. Processo de Mudança de Código

1.  **Desenvolvimento Isolado:** Nenhuma alteração é efetuada diretamente no ambiente de produção. Desenvolvedores devem trabalhar em ramificações (branches) isoladas no Git.
2.  **Revisão por Pares (Peer Review):** Todo Pull Request (PR) deve passar obrigatoriamente pela aprovação escrita de no mínimo um segundo desenvolvedor da equipe antes de qualquer merge.
3.  **Proteção de Branches:** As branches principais (`main`/`prod`) devem possuir regras de branch protection ativas para impedir merges sem aprovação ou com testes falhando.

---

## 3. Mudanças em Infraestrutura (IaC)

1.  **Implantação via IaC:** Mudanças em rede (VPCs, Security Groups) e infraestrutura de produção da AWS devem ser propostas como código (Terraform) e aplicadas exclusivamente pelo DevOps Marcelo Mascarenhas, sob aprovação escrita.
2.  **Planos de Rollback:** Deploys estruturais ou migrações de banco de dados devem conter um plano de rollback documentado e testado previamente em ambiente de Staging.

---

## 4. Revisão e Aprovação

Esta política é aprovada pela Diretoria Executiva da TWYN e revisada anualmente.

**Kacio Giuliano Lopes**  
CEO / Patrocinador Executivo  
TWYN T4ISB DO BRASIL TECNOLOGIA E PARTICIPACOES LTDA (CNPJ: 31.122.819/0001-55)
*Assinado eletronicamente via TWYN GRC Portal em 21/07/2026 18:00 BRT (IP: 189.122.34.55, Hash: bc87124ee418e0d10fa23b226e3aa74d)*
