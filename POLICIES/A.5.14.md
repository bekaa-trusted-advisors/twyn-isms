# POL-TX-001: Política de Transferência Segura de Informações — TWYN Face ID Platform
**ISO/IEC 27001:2022 Controle A.5.14 (Transferência de informação)**

---

**Controle de Documento**

| Campo | Valor |
|-------|-------|
| **Document ID** | POL-TX-001 |
| **Version** | 1.0 (Oficial) |
| **Autor** | Nizar Elouaer (CTO) |
| **Aprovador** | Kacio Giuliano Lopes (CEO) |
| **Data de Emissão** | 16/07/2026 |
| **Status** | Aprovado |

---

## 1. Objetivo

Garantir que as transferências de informações corporativas, arquivos de engenharia, credenciais e dados biométricos processados pela TWYN sejam efetuadas exclusivamente através de canais criptografados seguros, mitigando o risco de interceptações.

---

## 2. Protocolos de Comunicação Obrigatórios

1.  **Transferência de Arquivos:** Todo tráfego de dados corporativos ou arquivos de engenharia (como backups de bancos de dados ou logs) deve ocorrer exclusivamente por protocolos criptografados (ex: HTTPS ou SFTP com SSH Keys).
2.  **Criptografia Obrigatória:** Conexões externas de tráfego de API devem exigir TLS 1.3 habilitado. Conexões sem criptografia devem ser ativamente rejeitadas no Load Balancer.

---

## 3. Proibição de Plaintext e Compartilhamento Inseguro

1.  Fica terminantemente proibido compartilhar API Keys, chaves privadas, credenciais administrativas ou fotos faciais cruas por meios de comunicação de uso diário inseguros (ex: e-mail corporativo em plaintext, Slack, WhatsApp ou outros chats).
2.  Para compartilhamento pontual de credenciais entre a equipe técnica, deve-se utilizar exclusivamente os recursos internos do cofre de senhas (1Password) ou links seguros de visualização única gerados pelo cofre.

---

## 4. Revisão e Aprovação

Esta política é aprovada pela Diretoria Executiva da TWYN e revisada anualmente.

**Kacio Giuliano Lopes**  
CEO / Patrocinador Executivo  
TWYN T4ISB DO BRASIL TECNOLOGIA E PARTICIPACOES LTDA (CNPJ: 31.122.819/0001-55)
*Assinado eletronicamente via TWYN GRC Portal em 21/07/2026 18:00 BRT (IP: 189.122.34.55, Hash: e2cf8212d06b0b5226075214b6b6d35d)*
