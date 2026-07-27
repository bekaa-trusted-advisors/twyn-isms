# POL-SDP-001: Política de Desenvolvimento Seguro (SDLC) — TWYN Face ID Platform
**ISO/IEC 27001:2022 Controles A.8.25 (Ciclo de vida de desenvolvimento seguro) e A.8.31 (Segregação de ambientes de desenvolvimento, teste e produção)**

---

**Controle de Documento**

| Campo | Valor |
|-------|-------|
| **Document ID** | POL-SDP-001 |
| **Version** | 1.0 (Oficial) |
| **Autor** | Nizar Elouaer (CTO) |
| **Aprovador** | Kacio Lopes (CEO) |
| **Data de Emissão** | 16/07/2026 |
| **Status** | Aprovado |

---

## 1. Objetivo

Garantir que a segurança da informação e a privacidade de dados pessoais sejam integradas de ponta a ponta no ciclo de vida de desenvolvimento de software (SDLC) da API da TWYN.

---

## 2. Segregação de Ambientes (A.8.31)

1.  **Isolamento de Contas AWS:** Os ambientes de Desenvolvimento (`Dev`), Homologação/QA (`Staging`) e Produção (`Prod`) devem residir em contas AWS totalmente separadas sob a AWS Organizations.
2.  **Isolamento de Redes:** Cada conta AWS opera sua própria VPC com sub-redes privadas e isoladas, sem Peering direto ou caminhos de rede não autorizados entre Desenvolvimento e Produção.
3.  **Proibição de Dados de Produção em Testes:** Fica expressamente proibido copiar hashes biométricos de produção para os ambientes de desenvolvimento. Testes devem utilizar dados sintéticos ou dados anonimizados.

---

## 3. Diretrizes de Ciclo de Desenvolvimento Seguro (A.8.25)

1.  **Requisitos de Segurança:** Requisitos de conformidade e proteção de biometria devem ser definidos no escopo técnico de cada feature antes do início de codificação.
2.  **Varreduras de Vulnerabilidades (DevSecOps Pipeline):**
    *   *SAST (Static Application Security Testing):* Rodar Semgrep ou SonarQube no pipeline de CI/CD para detectar código inseguro.
    *   *SCA (Software Composition Analysis):* Manter ativo o Dependabot para identificar dependências vulneráveis (CVEs).
3.  **Gates de Qualidade (Quality Gates):** O pipeline de CI/CD deve bloquear automaticamente deploys para Homologação ou Produção se contiver vulnerabilidades classificadas como **High** ou **Critical** sem justificativa formal aprovada pelo CTO Nizar Elouaer.

---

## 4. Revisão e Aprovação

Esta política é aprovada pela Diretoria Executiva da TWYN e revisada anualmente.

**Kacio Lopes**  
CEO / Patrocinador Executivo  
TWYN T4ISB DO BRASIL TECNOLOGIA E PARTICIPACOES LTDA (CNPJ: 31.122.819/0001-55)
*Assinado eletronicamente via TWYN GRC Portal em 21/07/2026 18:00 BRT (IP: 189.122.34.55, Hash: 780ab594539d04bb8a8359805d86085c)*
