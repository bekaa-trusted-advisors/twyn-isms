# Relatório de Conformidade Contratual de Privacidade (DPA/LGPD) — AWS

> **Controle ISO/IEC 27701:2019:** Cláusula 7.2.4 (Diligência com operadores/fornecedores) & Cláusula 6.13.1.2 (Transferências internacionais de PII)  
> **Conformidade Legal:** Artigo 33 (Transferência Internacional) & Artigo 39 (Responsabilidade do Operador) da LGPD  
> **Status:** `EM CONFORMIDADE`

> ⚠️ **Correção de escopo (ENG-2026-001, 2026-08-24):** este documento foi originalmente redigido sob a
> premissa de que os dados residiam em `us-east-1` (EUA), com transferência internacional amparada por
> cláusulas-padrão. **O dado real reside em `sa-east-1` (São Paulo, Brasil)** — portanto **não há
> transferência internacional** e a seção 2 abaixo (transferência internacional/SCC) **não se aplica**.
> O DPA com a AWS permanece válido como acordo de proteção de dados operador-controlador (LGPD Art. 39).

Este documento registra a análise técnica de conformidade contratual de privacidade efetuada pela governança da Twyn no adendo de processamento de dados da **Amazon Web Services (AWS)**.

---

## ⚖️ 1. Enquadramento de Papéis e Responsabilidades (LGPD/GDPR)

Conforme estabelecido nos termos do **Data Processing Addendum (DPA)** incorporado de forma automática e vinculativa aos Termos de Serviço da AWS:

*   **Twyn (Cliente):** Atua como **Controlador de Dados** (*Data Controller*). Retém a propriedade e o controle absoluto sobre as finalidades, meios de tratamento e o conteúdo dos dados pessoais tratados (vetores biométricos faciais).
*   **AWS:** Atua como **Operador de Dados / Subprocessador** (*Data Processor / Sub-processor*). Trata as informações inseridas pela Twyn exclusivamente conforme as instruções documentadas do controlador e em conformidade com as regras técnicas configuradas.

---

## 🌍 2. Localização dos Dados (sem transferência internacional)

Os recursos computacionais da AWS que servem à Face ID API estão hospedados na região **`sa-east-1` (São Paulo, Brasil)**:

1.  **Território nacional:** os dados pessoais (vetores biométricos) permanecem no Brasil — **não há transferência internacional** e, portanto, **não se aplica** o regime dos Arts. 33–36 da LGPD.
2.  **DPA vigente:** o Data Processing Addendum da AWS permanece válido como acordo operador-controlador (obrigações de confidencialidade, auditoria, notificação de incidentes e proteção dos direitos dos titulares — LGPD Art. 39).
3.  _(Correção ENG-2026-001: a redação anterior tratava de transferência internacional para os EUA (`us-east-1`), o que não corresponde à localização real dos dados.)_

---

## 🔒 3. Controles Técnicos de Privacidade Incorporados

O adendo contratual assegura à Twyn autonomia de segurança por padrão (*Privacy by Design* e *Privacy by Default*):

*   **Políticas de Acesso Restritivas (Negação por Padrão):** AWS opera sob arquitetura de negação por padrão para todas as chamadas de API (exceto credenciais raiz explicitamente concedidas), permitindo à Twyn restringir o acesso geográfico via políticas de `aws:RequestedRegion` (pág. 17).
*   **Cofres de Chaves e Criptografia Isolada (KMS):** A AWS não possui acesso às chaves de criptografia e decodificação geradas pela Twyn no AWS KMS que protegem os volumes de banco de dados RDS (pág. 31). A criptografia de envelope impede que funcionários do provedor de nuvem visualizem dados biométricos em texto puro.
*   **Isolamento e SDLC:** O conteúdo do cliente não é utilizado pela AWS para fins de treinamento de software ou ciclos de desenvolvimento e homologação de plataformas secundárias (pág. 52).

---

## 📈 4. Parecer de Homologação de Privacidade

O DPA da AWS é considerado **aprovado e em plena conformidade** com os requisitos do SGPI (ISO 27701) da Twyn. Os mecanismos contratuais estabelecidos garantem a blindagem jurídica necessária frente à ANPD e parceiros comerciais B2B, assegurando que o tratamento de biometria facial atenda aos princípios de necessidade, finalidade e segurança técnica.

---

## 📅 Histórico de Revisão

*   **Elaborado por:** Ricardo Esper (Consultor SGSIP)
*   **Aprovado por:** Kacio Lopes (CEO)
*   **Data de Homologação:** 2026-07-27
*   **Revisão:** Anual
