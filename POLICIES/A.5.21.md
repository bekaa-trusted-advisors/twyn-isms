# POL-SUP-001: Política de Segurança em Relacionamento com Fornecedores — TWYN

**ISO/IEC 27001:2022 Controles A.5.19 (Segurança da informação no relacionamento com fornecedores), A.5.20 (Tratamento da segurança da informação em acordos com fornecedores), A.5.21 (Gestão da segurança da informação na cadeia de suprimentos de TIC) e A.5.22 (Monitoramento, análise crítica e gestão de mudanças de serviços de fornecedores) | ISO/IEC 27701:2025 Anexo A: A.3.10 (Cadeia de suprimento) e A.1.2.7 (Contratos com operadores de DP)**

---

**Controle de Documento**

| Campo | Valor |
|-------|-------|
| **Document ID** | POL-SUP-001 |
| **Version** | 1.0 (Oficial) |
| **Elaborado por** | Enes Degasperi (CFO / Financeiro) |
| **Aprovado por** | Nizar Elouaer (CTO / Liderança Executiva de SI) |
| **Data de Emissão** | 21/07/2026 |
| **Status** | `Aprovado` |

---

## 1. Requisitos Mínimos de Segurança da Informação (A.5.19, A.5.20)

Todos os fornecedores de tecnologia e serviços que possuem acesso lógico a dados da TWYN, ou que hospedam infraestrutura do ecossistema Face ID Platform, devem atender aos seguintes requisitos de conformidade contratual:

1.  **Exigências de Certificação:** Provedores de alta criticidade (ex: datacenters, serviços SaaS críticos) devem preferencialmente possuir relatório SOC 2 Tipo II ou certificação ISO/IEC 27001 vigente.
2.  **Acordos de Tratamento de Dados (DPA):** É obrigatória a assinatura de aditivos contratuais de privacidade (DPAs) estabelecendo obrigações rígidas de proteção de dados pessoais e responsabilidades como subprocessadores sob a LGPD.
3.  **Cláusulas de Notificação de Incidentes:** Os contratos devem prever que o fornecedor notifique a TWYN sobre qualquer incidente de segurança suspeito ou confirmado em até **24 horas** após a descoberta técnica do fato.

---

## 2. Processo Formal de Homologação de Fornecedores (A.5.21)

A homologação de novos fornecedores de tecnologia de informação e comunicação (TIC) na TWYN segue os passos estruturados abaixo:

1.  **Questionário KYV (Know Your Vendor):** O fornecedor sob avaliação deve preencher o formulário KYV de privacidade e segurança da informação.
2.  **Análise de Risco:** O Encarregado (DPO), Bekaa Tecnologia Ltda (PJ), analisa as respostas do formulário, classificando o fornecedor como Risco Alto (acesso a biometria/código), Médio (acesso a logs de negócio) ou Baixo (acesso administrativo geral).
3.  **Parecer de Homologação:** A contratação é liberada formalmente pelo CFO Enes Degasperi apenas após parecer técnico de privacidade sem ressalvas impeditivas.

---

## 3. Monitoramento Contínuo e Auditorias de Terceiros (A.5.22)

Para assegurar a conformidade contínua dos parceiros críticos contratados:

1.  **Auditorias e Revisões Anuais:** A TWYN conduz auditorias periódicas anuais para verificar se fornecedores de alta criticidade (como consultorias terceirizadas de engenharia de software) estão mantendo os padrões exigidos.
2.  **Revisão de Relatórios de Terceiros:** O time de segurança da TWYN revisa anualmente os relatórios SOC 2 Tipo II e certificados ISO 27001 dos principais provedores de nuvem (AWS), mantendo o histórico de análise devidamente arquivado.
3.  **Ações Corretivas (CAPAs):** Qualquer não conformidade detectada em fornecedores acarretará a formalização de um plano de remediação com prazo máximo de 30 dias para correção pelo parceiro.

---

## 4. Matriz de Auditoria de Fornecedores por Categoria (Vendor Risk Tiering)

A classificação e os procedimentos de auditoria para fornecedores de TIC na TWYN seguem uma abordagem baseada em risco (ISO 19011:2026 A.12):

### Categoria Tier 1: Provedores Hyperscale & Big Techs
*   **Exemplos:** AWS, Cloudflare, GitHub, OpenAI, Google Cloud, Vercel.
*   **Característica:** Provedores de infraestrutura crítica altamente padronizados e sem canal de atendimento para formulários customizados.
*   **Método de Auditoria:** Validação automatizada via portais oficiais de transparência (Self-Service Trust Portals).
*   **Procedimento Operacional:**
    1. Acesso ao portal oficial de conformidade do provedor (ex: AWS Artifact, GitHub Trust Center).
    2. Download anual do Certificado ISO 27001/27017/27018 e Relatório SOC 2 Tipo II ou SOC 3 vigentes.
    3. Registro da data de validade e arquivamento das evidências objetivas no nISO (Controle A.5.22).
*   **Esforço exigido do fornecedor:** Zero (100% automatizado pela TWYN).

### Categoria Tier 2: Provedores SaaS de Médio Porte & Ferramentas Operacionais
*   **Exemplos:** Linear, Datadog, Slack, 1Password, PagerDuty.
*   **Característica:** Ferramentas SaaS consolidadas de mercado com políticas públicas de segurança claras.
*   **Método de Auditoria:** Análise de certificações públicas ou aplicação de Questionário KYV Sintético.
*   **Procedimento Operacional:**
    1. Verificação anual da página de segurança pública (`/security`) do fornecedor em busca de SOC 2 Tipo II ou ISO 27001 ativa.
    2. Solicitação da síntese executiva do último relatório de PenTest sob NDA, caso o sistema armazene dados pessoais de usuários da TWYN.
    3. Envio de questionário KYV sintético (8 a 10 perguntas objetivas focadas em criptografia, backup e controle de acesso) caso o fornecedor não possua certificações SOC 2 ou ISO.

### Categoria Tier 3: Consultorias, Desenvolvedores Terceirizados e Prestadores de Serviços Pessoais
*   **Exemplos:** Consultorias de desenvolvimento de software, prestadores de suporte técnico, advogados externos ou terceiros alocados.
*   **Característica:** Alto risco regulatório e operacional por possuírem credenciais lógicas e acessos diretos ao código-fonte, bancos de staging ou logs.
*   **Método de Auditoria:** Questionário KYV Completo (25 perguntas) + Salvaguardas Contratuais + Recertificação Trimestral de Acesso.
*   **Procedimento Operacional:**
    1. Mapeamento e aplicação obrigatória do formulário KYV completo de 25 perguntas avaliando práticas de segurança física e lógica na contratação.
    2. Assinatura obrigatória de NDA de no mínimo 5 anos e aditivos de DPA contratuais da LGPD com dever de notificação de incidentes em até 24 horas.
    3. Exigência contratual de que o prestador realize *background checks* (A.6.1) em seus próprios colaboradores alocados no projeto TWYN.
    4. Revisão trimestral de acessos lógicos e Pull Requests (recertificação de acessos).

### Resumo de Exigências e Periodicidade

| Categoria do Fornecedor | Requisito Exigido de Evidência | Periodicidade de Revisão |
| :--- | :--- | :--- |
| **Tier 1 (Hyperscale)** | Certificado ISO 27001 / SOC 2 Tipo II baixado do Trust Center | Anual |
| **Tier 2 (SaaS Médio)** | Relatório SOC 2 ou Questionário KYV Sintético (10 perguntas) | Anual |
| **Tier 3 (Terceiros/Devs)** | Questionário KYV Completo + NDA + Aditivo DPA Contratual | Na Contratação + Revisão Anual |

---

## 5. Homologação

**Nizar Elouaer**  
CTO / Liderança Executiva de SI  
TWYN T4ISB DO BRASIL TECNOLOGIA E PARTICIPACOES LTDA (CNPJ: 31.122.819/0001-55)
*Assinado eletronicamente via TWYN GRC Portal em 21/07/2026 18:00 BRT (IP: 191.189.44.112, Hash: 8bffa8916b683bd0de1494fbe2b679e4)*
