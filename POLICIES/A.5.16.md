# POL-ACP-001: Política de Controle de Acesso e Identidades — TWYN Face ID Platform
**ISO/IEC 27001:2022 Controles A.5.15 (Controle de acesso), A.5.16, A.5.17, A.5.18, A.8.3 e A.8.4**

---

**Controle de Documento**

| Campo | Valor |
|-------|-------|
| **Document ID** | POL-ACP-001 (POL-IAM-002) |
| **Version** | 1.0 (Oficial) |
| **Autor** | Ricardo Esper (Consultor) |
| **Aprovador** | Kacio Lopes (CEO) |
| **Data de Emissão** | 16/07/2026 |
| **Status** | Aprovado |

---

## 1. Objetivo

Definir as diretrizes para o controle de acesso lógico e gerenciamento de identidades na TWYN, garantindo o princípio do menor privilégio e a segregação de funções.

---

## 2. Diretrizes de Gestão de Identidades e SSO (A.5.15, A.5.16)

1.  **SSO Centralizado:** O acesso a ferramentas SaaS corporativas e ambientes em nuvem (Slack, GitHub, AWS, Datadog) deve ser centralizado e autenticado por meio do Provedor de Identidade (IdP) Okta/Auth0.
2.  **Ciclo de Vida de Acessos:** A concessão ou alteração de acessos lógicos deve ser aprovada formalmente pela Diretoria de Identidade, Acesso e Segurança (CPO Humberto Oliveira) e executada pelo time de DevOps. Em caso de desligamento, o RH deve notificar o DevOps para revogar todos os acessos lógicos em até **2 horas úteis** (conforme `POL-HR-001`).

---

## 3. Requisitos de Autenticação Segura (A.5.17)

1.  **Complexidade de Senha:** Qualquer senha de acesso ao IdP corporativo ou AWS Console deve conter no mínimo 14 caracteres, incluindo letras maiúsculas, minúsculas, números e caracteres especiais.
2.  **MFA Obrigatório:** O segundo fator de autenticação (MFA) é obrigatório para todos os acessos de colaboradores e consultores externos, sem exceções.
3.  **Cofre de Senhas:** Fica proibida a gravação de senhas em plaintext. É obrigatória a utilização do cofre de senhas corporativo (1Password/AWS Secrets Manager) para compartilhamento seguro de credenciais administrativas.

---

## 4. Revisão Periódica de Direitos de Acesso (A.5.18)

1.  A Diretoria de Identidade, Acesso e Segurança (CPO Humberto Oliveira) deve realizar a auditoria completa de acessos concedidos nas contas AWS e ferramentas SaaS corporativas a cada **6 meses**, revogando imediatamente privilégios excessivos ou de contas inativas.

---

## 5. Restrições Lógicas específicas da API (A.8.3, A.8.4)

1.  **Acesso a Dados Biométricos (A.8.3):** O acesso a dados biométricos (Face templates no banco RDS Aurora) deve ser restrito exclusivamente a chamadas automatizadas da API Face ID. Nossos engenheiros não possuem acesso a dados biométricos de produção.
2.  **Acesso a Código-Fonte (A.8.4):** O acesso de escrita e visualização aos repositórios do código-fonte da API no GitHub deve ser restrito a desenvolvedores autorizados. As branches `main`/`prod` devem possuir regras de proteção rígidas (exigência de Pull Request com aprovação de 1 revisor independente e testes de CI/CD verdes).

---

## 6. Revisão e Aprovação

Esta política é aprovada pela Diretoria Executiva da TWYN e revisada anualmente.

**Kacio Lopes**  
CEO / Patrocinador Executivo  
TWYN T4ISB DO BRASIL TECNOLOGIA E PARTICIPACOES LTDA (CNPJ: 31.122.819/0001-55)
*Assinado eletronicamente via TWYN GRC Portal em 21/07/2026 18:00 BRT (IP: 189.122.34.55, Hash: 0f383de0ecd0ca82ee8b49bd2e5590d0)*
