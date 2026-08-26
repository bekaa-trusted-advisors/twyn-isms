# Declaração de Aplicabilidade (SoA) — TWYN Face ID Platform

> **Referência Normativa:** ABNT NBR ISO/IEC 27001:2022 (Anexo A). Extensão de privacidade (27701) tratada em `soa/SGPI-SoA-27701-2025.md`.  
> **Status Geral do SGSI (espelho do nISO, 2026-08-26):** `Em Adequação` — **23 Implemented · 47 In Progress · 5 Missing · 3 Planned · 15 Not Applicable** (93 controles; 78 aplicáveis).

> **Reconciliação ENG-2026-001 (2026-08-26) — `SOA.md` alinhado à fonte da verdade (nISO):** o status,
> o proprietário e os resíduos de "CISO" de **todos os 93 controles** foram **regenerados a partir do
> nISO** (projeto `mr9c1qugo16zic2eko`). Onde o repo declarava `Implemented` sem lastro no nISO, o
> status foi **rebaixado para o real** (majoritariamente `In Progress` = implementado, pendente de
> evidência de operação); onde o repo estava atrasado, foi **elevado** ao nISO. A elevação de
> `In Progress → Implemented` cabe à **auditoria interna 9.2** (verificação de operação efetiva), não a
> esta reconciliação documental. **Nenhuma conformidade foi presumida.**

Esta Declaração de Aplicabilidade cataloga os 93 controles de segurança do Anexo A da ISO/IEC 27001:2022, definindo aplicabilidade, status de implementação, nível de maturidade e proprietários técnicos. Os controles específicos de privacidade da ISO/IEC 27701:2025 são tratados na extensão do SGPI (`soa/SGPI-SoA-27701-2025.md`).

---

## Tabela de Controles do SGSI/SGPI

| ID Controle | Título do Controle | Status | Maturidade (CMM) | Proprietário | Justificativa / Documentação de Suporte |
|---|---|---|---|---|---|
| **A.51** | A.5.1 Políticas de Segurança da Informação | `In Progress` | 4 | CIO / Resp. Segurança | POL-ISP-001: Política de Segurança da Informação — TWYN Face ID Platform**ISO/IEC 27001:2022 Controle A.5.1 (Políticas para segurança da informação)**... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.52** | A.5.2 Papéis e Responsabilidades de Segurança da Informação | `In Progress` | 4 | CIO / Resp. Segurança | Required for clear accountability.... |
| **A.53** | A.5.3 Segregação de Funções | `In Progress` | 3 | CIO / Resp. Segurança | Matriz RACI (SGSI-RACI-001) define a segregação de funções de governança e operacionais.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.54** | A.5.4 Responsabilidades da Direção | `In Progress` | 3 | CIO / Resp. Segurança | Política POL-GOV-001 define as responsabilidades gerenciais do comitê.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.55** | A.5.5 Contato com Autoridades | `In Progress` | 3 | CIO / Resp. Segurança | Matriz de contatos com a ANPD e delegacia de crimes cibernéticos em POL-IRP-001.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.56** | A.5.6 Contato com Grupos Especiais de Interesse | `In Progress` | 3 | CIO / Resp. Segurança | Afiliação e canais de inteligência de ameaças com o CERT.br e ANPPD definidos na POL-IRP-001.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.57** | A.5.7 Inteligência sobre Ameaças | `In Progress` | 3 | CIO / Resp. Segurança | Feeds de ameaças do AWS GuardDuty e indicadores de compromisso (IoCs) do MISP integrados na POL-THR-001.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.58** | A.5.8 Segurança da Informação na Gestão de Projetos | `In Progress` | 3 | CIO / Resp. Segurança | Segurança em projetos atrelada aos templates de Jira na POL-GOV-001.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.59** | A.5.9 Inventário de Informações e Outros Ativos Associados | `In Progress` | 4 | IT Manager | Inventário de ativos migrado para a tabela assets dedicada.... |
| **A.61** | A.6.1 Seleção de Pessoas | `Implemented` | 0 | CIO / Resp. Segurança | Background verification for all personnel.... |
| **A.62** | A.6.2 Termos e Condições de Contratação | `Implemented` | 0 | CIO / Resp. Segurança | Security responsibilities in employment contracts.... |
| **A.63** | A.6.3 Conscientização, Educação e Treinamento em Segurança da Informação | `Implemented` | 4 | CIO / Resp. Segurança | Security awareness is universal.... — ENG-2026-001: EVICERT (Ata de Homologação + certificados de treinamento SI/LGPD, 7 colaboradores, 100%, 11 tópicos) |
| **A.64** | A.6.4 Processo Disciplinar | `Implemented` | 0 | CIO / Resp. Segurança | Consequences for policy violations.... |
| **A.65** | A.6.5 Responsabilidades Pós-Desligamento ou Mudança de Emprego | `In Progress` | 3 | CIO / Resp. Segurança | Processo de revogação de credenciais em 2h e termo de offboarding em POL-HR-001.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.66** | A.6.6 Acordos de Confidencialidade e Não Divulgação (NDAs) | `Implemented` | 4 | CIO / Resp. Segurança | Assinatura obrigatória de NDA de admissão com validade de 5 anos.... (Aprovado por CEO Kacio Giuliano Lopes) — ENG-2026-001: EVITERMOS/EVIPRO04 (Termos de sigilo/responsabilidade, 100% dos colaboradores) |
| **A.67** | A.6.7 Trabalho Remoto | `Implemented` | 0 | CIO / Resp. Segurança | Remote work arrangements identified.... — ENG-2026-001: POL-RMT-001 (A.6.7) — trabalho remoto; **aplicável** (equipe 100% remota) |
| **A.68** | A.6.8 Notificação de Eventos de Segurança da Informação | `Implemented` | 0 | CIO / Resp. Segurança | All personnel must be able to report events.... |
| **A.71** | A.7.1 Perímetros de Segurança Física | `Not Applicable` | 0 | CIO / Resp. Segurança | Excluído: Equipe opera 100% remoto sem escritório físico e infraestrutura hospedada inteiramente na nuvem AWS (modelo de responsabilidade compartilhad... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.72** | A.7.2 Entrada Física | `Not Applicable` | 0 | CIO / Resp. Segurança | Excluído: Equipe opera 100% remoto sem escritório físico e infraestrutura hospedada inteiramente na nuvem AWS (modelo de responsabilidade compartilhad... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.73** | A.7.3 Proteção de Escritórios, Salas e Instalações | `Not Applicable` | 0 | CIO / Resp. Segurança | Excluído: Equipe opera 100% remoto sem escritório físico e infraestrutura hospedada inteiramente na nuvem AWS (modelo de responsabilidade compartilhad... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.74** | A.7.4 Monitoramento da Segurança Física | `Not Applicable` | 0 | CIO / Resp. Segurança | Excluído: Equipe opera 100% remoto sem escritório físico e infraestrutura hospedada inteiramente na nuvem AWS (modelo de responsabilidade compartilhad... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.75** | A.7.5 Proteção Contra Ameaças Físicas e Ambientais | `Not Applicable` | 0 | CIO / Resp. Segurança | Excluído: Equipe opera 100% remoto sem escritório físico e infraestrutura hospedada inteiramente na nuvem AWS (modelo de responsabilidade compartilhad... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.76** | A.7.6 Trabalho em Áreas Seguras | `Not Applicable` | 0 | CIO / Resp. Segurança | Excluído: Equipe opera 100% remoto sem escritório físico e infraestrutura hospedada inteiramente na nuvem AWS (modelo de responsabilidade compartilhad... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.77** | A.7.7 Mesa Limpa e Tela Limpa | `Not Applicable` | 0 | CIO / Resp. Segurança | Applies to all workstations including remote.... |
| **A.78** | A.7.8 Localização e Proteção de Equipamentos | `Not Applicable` | 0 | CIO / Resp. Segurança | Excluído: Equipe opera 100% remoto sem escritório físico e infraestrutura hospedada inteiramente na nuvem AWS (modelo de responsabilidade compartilhad... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.79** | A.7.9 Segurança de Ativos Fora das Instalações | `Not Applicable` | 0 | CIO / Resp. Segurança | Assets used outside premises require protection.... |
| **A.81** | A.8.1 Dispositivos de Usuário Final | `Implemented` | 0 | CIO / Resp. Segurança | Endpoint security is universally required.... — ENG-2026-001: POL-EPP-001 (A.8.1) — endpoints |
| **A.82** | A.8.2 Direitos de Acesso Privilegiado | `In Progress` | 3 | CIO / Resp. Segurança | Controle de acessos privilegiados (admins) na AWS e sistemas críticos restritos a perfis específicos revisados periodicamente.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.83** | A.8.3 Restrição de Acesso à Informação | `In Progress` | 3 | CIO / Resp. Segurança | Restrição granular a dados biométricos sensíveis e aplicação de RBAC.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.84** | A.8.4 Acesso ao Código-Fonte | `In Progress` | 3 | CIO / Resp. Segurança | Branch protection ativa e restrição de acesso ao repositório GitHub da API.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.85** | A.8.5 Autenticação Segura | `In Progress` | 4 | CIO / Resp. Segurança | Obrigatoriedade de autenticação multifator (MFA) em contas AWS e consoles administrativos.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.86** | A.8.6 Gestão de Capacidade | `Implemented` | 0 | CIO / Resp. Segurança | Resource capacity planning is universal.... — ENG-2026-001: SGP-CAP-001 (A.8.6) — gestão de capacidade |
| **A.87** | A.8.7 Proteção contra Malware | `Implemented` | 0 | CIO / Resp. Segurança | Malware protection is universally required.... — ENG-2026-001: POL-MAL-001 (A.8.7) — proteção contra malware |
| **A.88** | A.8.8 Gestão de Vulnerabilidades Técnicas | `In Progress` | 4 | CIO / Resp. Segurança | Vulnerability management is universal.... |
| **A.89** | A.8.9 Gestão de Configuração | `In Progress` | 3 | CIO / Resp. Segurança | Manual SOP-HDN-001 define os baselines de hardening para RDS e EKS.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.510** | A.5.10 Uso Aceitável de Informações e Outros Ativos Associados | `In Progress` | 4 | CIO / Resp. Segurança | Defines acceptable behavior for all personnel.... |
| **A.511** | A.5.11 Devolução de Ativos | `In Progress` | 3 | CIO / Resp. Segurança | POL-HR-001 impõe a devolução de notebooks e chaves de acesso em até 2 dias.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.512** | A.5.12 Classificação da Informação | `In Progress` | 3 | CIO / Resp. Segurança | Política POL-GOV-001 de classificação de informações biométricas implementada.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.513** | A.5.13 Rotulagem da Informação | `In Progress` | 3 | CIO / Resp. Segurança | Rotulagem de dados biométricos sensíveis aplicada via tagging AWS e tags em banco de dados.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.514** | A.5.14 Transferência de Informações | `In Progress` | 3 | CIO / Resp. Segurança | POL-TX-001 define o uso exclusivo de HTTPS/SFTP e proíbe plaintext de dados sensíveis.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.515** | A.5.15 Controle de Acesso | `Planned` | 4 | CIO / Resp. Segurança | Logical access control is universally required.... |
| **A.516** | A.5.16 Gestão de Identidades | `In Progress` | 3 | CIO / Resp. Segurança | SSO Okta/Auth0 centraliza o acesso de colaboradores da TWYN a ferramentas SaaS.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.517** | A.5.17 Informações de Autenticação | `In Progress` | 3 | DevOps | Padrão de complexidade de senhas do IdP e uso de cofre 1Password regulados.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.518** | A.5.18 Direitos de Acesso | `In Progress` | 3 | CIO / Resp. Segurança | Revisão semestral de acessos e concessão sob demanda aprovada pela liderança de segurança (CIO).... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.519** | A.5.19 Segurança da Informação no Relacionamento com Fornecedores | `In Progress` | 5 | CIO / Resp. Segurança | Third-party/vendor relationships identified.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.520** | A.5.20 Tratamento da Segurança da Informação nos Acordos com Fornecedores | `In Progress` | 5 | CIO / Resp. Segurança | Contractual security clauses needed for suppliers.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.521** | A.5.21 Gestão da Segurança da Informação na Cadeia de Suprimentos de TIC | `In Progress` | 3 | CIO / Resp. Segurança | Questionário KYV implementado para qualificação de segurança de fornecedores de TIC críticos.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.522** | A.5.22 Monitoramento, Análise Crítica e Gestão de Mudanças de Serviços de Fornecedores | `In Progress` | 3 | CIO / Resp. Segurança | Revisão contratual anual conduzida pelo CFO Enes Degasperi.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.523** | A.5.23 Segurança da Informação no Uso de Serviços em Nuvem | `Implemented` | 0 | CIO / Resp. Segurança | Cloud infrastructure in use.... — ENG-2026-001: POL-CLD-001 (A.5.23) — nuvem AWS; **aplicável** (infra 100% AWS) |
| **A.524** | A.5.24 Planejamento e Preparação da Gestão de Incidentes de Segurança da Informação | `In Progress` | 4 | CIO / Resp. Segurança | Incident preparedness is universal.... |
| **A.525** | A.5.25 Avaliação e Decisão sobre Eventos de Segurança da Informação | `Implemented` | 0 | CIO / Resp. Segurança | Event triage process required.... |
| **A.526** | A.5.26 Resposta a Incidentes de Segurança da Informação | `In Progress` | 3 | CIO / Resp. Segurança | Fases de contenção, erradicação e pós-mortem detalhadas no workflow da POL-IRP-001.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.527** | A.5.27 Aprendizado com Incidentes de Segurança da Informação | `Implemented` | 0 | CIO / Resp. Segurança | Continuous improvement from incidents.... — ENG-2026-001: SGP-IRL-001 (A.5.27) — aprendizado com incidentes |
| **A.528** | A.5.28 Coleta de Evidências | `Implemented` | 0 | CIO / Resp. Segurança | Evidence preservation for investigations.... |
| **A.529** | A.5.29 Segurança da Informação em Momentos de Interrupção | `Planned` | 4 | CIO / Resp. Segurança | Security continuity during disruptions.... |
| **A.530** | A.5.30 Prontidão da TIC para a Continuidade dos Negócios | `In Progress` | 4 | IT Manager | BCP Elaborado. RTO: 4 horas, RPO: 1 hora. Restore RDS testado em sandbox.... |
| **A.531** | A.5.31 Requisitos Legais, Estatutários, Regulamentares e Contratuais | `In Progress` | 0 | CIO / Resp. Segurança | Compliance obligations exist for all organizations.... |
| **A.532** | A.5.32 Direitos de Propriedade Intelectual | `Implemented` | 0 | CIO / Resp. Segurança | IP protection applies to all organizations.... — ENG-2026-001: POL-IPR-001 (A.5.32) — propriedade intelectual |
| **A.533** | A.5.33 Proteção de Registros | `In Progress` | 4 | CIO / Resp. Segurança | POL-GOV-001 define a retenção de templates de face ligada ao contrato e descarte seguro em 15 dias.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.534** | A.5.34 Privacidade e Proteção de Dados Pessoais (PII) | `In Progress` | 5 | CIO / Resp. Segurança | PII processing identified — privacy controls mandatory.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.535** | A.5.35 Análise Crítica Independente da Segurança da Informação | `Planned` | 0 | CIO / Resp. Segurança | Independent assurance is an ISMS requirement.... — ENG-2026-001: POL-REV-001 (A.5.35) — execução = auditoria 9.2 independente (issue #17), pendente |
| **A.536** | A.5.36 Conformidade com Políticas, Regras e Normas de Segurança da Informação | `Implemented` | 0 | CIO / Resp. Segurança | Compliance verification is universal.... — ENG-2026-001: SGP-CMP-001 (A.5.36) — verificação de conformidade |
| **A.537** | A.5.37 Procedimentos Operacionais Documentados | `Implemented` | 0 | CIO / Resp. Segurança | Operational procedures must be documented.... — ENG-2026-001: POL-OPS-001 (A.5.37) — procedimentos operacionais |
| **A.710** | A.7.10 Mídias de Armazenamento | `Not Applicable` | 0 | CIO / Resp. Segurança | Media handling applies to all organizations.... |
| **A.711** | A.7.11 Utilidades de Suporte | `Not Applicable` | 0 | CIO / Resp. Segurança | Excluído: Equipe opera 100% remoto sem escritório físico e infraestrutura hospedada inteiramente na nuvem AWS (modelo de responsabilidade compartilhad... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.712** | A.7.12 Segurança do Cabeamento | `Not Applicable` | 0 | CIO / Resp. Segurança | Excluído: Equipe opera 100% remoto sem escritório físico e infraestrutura hospedada inteiramente na nuvem AWS (modelo de responsabilidade compartilhad... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.713** | A.7.13 Manutenção de Equipamentos | `Not Applicable` | 0 | CIO / Resp. Segurança | All equipment requires maintenance.... |
| **A.714** | A.7.14 Descarte ou Reutilização Segura de Equipamentos | `Not Applicable` | 0 | CIO / Resp. Segurança | Secure disposal applies universally.... |
| **A.810** | A.8.10 Exclusão de Informação | `In Progress` | 5 | CIO / Resp. Segurança | Data lifecycle management is universal.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.811** | A.8.11 Mascaramento de Dados | `Missing` | 4 | CIO / Resp. Segurança | Sensitive/PII data requires masking in non-production.... |
| **A.812** | A.8.12 Prevenção de Vazamento de Dados (DLP) | `Missing` | 4 | CIO / Resp. Segurança | DLP needed for sensitive/regulated data.... |
| **A.813** | A.8.13 Backup da Informação | `In Progress` | 4 | CIO / Resp. Segurança | AWS Backup configurado com políticas de retenção rígidas. RTO de 4h e RPO de 1h validados em testes semestrais.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.814** | A.8.14 Redundância dos Recursos de Processamento de Informação | `In Progress` | 3 | CIO / Resp. Segurança | EKS distribuído em 3 AZs e replicação de RDS Aurora em Multi-AZ.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.815** | A.8.15 Registros de Log | `Missing` | 5 | DevOps | Monitoramento contínuo via AWS CloudTrail e GuardDuty.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.816** | A.8.16 Atividades de Monitoramento | `Missing` | 4 | CIO / Resp. Segurança | Security monitoring is universal.... |
| **A.817** | A.8.17 Sincronização do Relógio | `Implemented` | 0 | CIO / Resp. Segurança | Time synchronization for log correlation.... — ENG-2026-001: SGP-NTP-001 (A.8.17) — sincronização de relógio |
| **A.818** | A.8.18 Uso de Programas Utilitários Privilegiados | `Implemented` | 0 | CIO / Resp. Segurança | Restricting privileged utilities is universal.... — ENG-2026-001: SGP-PUP-001 (A.8.18) — utilitários privilegiados |
| **A.819** | A.8.19 Instalação de Software em Sistemas Operacionais | `Implemented` | 0 | CIO / Resp. Segurança | Software installation controls are universal.... |
| **A.820** | A.8.20 Segurança de Redes | `In Progress` | 3 | CIO / Resp. Segurança | Redes segregadas logicamente e monitoradas com regras de firewall/Security Groups ativas.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.821** | A.8.21 Segurança dos Serviços de Rede | `In Progress` | 3 | CIO / Resp. Segurança | Serviços de rede protegidos. Acesso administrativo restrito via Bastion Host e VPN.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.822** | A.8.22 Segregação de Redes | `In Progress` | 3 | DevOps | Segregação de redes via VPC e Security Groups (SOP-004).... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.823** | A.8.23 Filtragem Web | `Missing` | 4 | CIO / Resp. Segurança | Aplicado e monitorado nos endpoints corporativos dos colaboradores via soluções de MDM/Antivírus de proteção contra ameaças web.... |
| **A.824** | A.8.24 Uso de Criptografia | `In Progress` | 4 | CIO / Resp. Segurança | ## Objetivo A política de segurança da informação para o controle A.8.24 da TWYN T4ISB DO BRASIL TECNOLOGIA E PARTICIPACOES LTDA visa garantir a imple... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.825** | A.8.25 Ciclo de Vida de Desenvolvimento Seguro (SDLC) | `In Progress` | 4 | CIO / Resp. Segurança | ## Objetivo A política de segurança da informação para o controle A.8.25 da TWYN T4ISB DO BRASIL TECNOLOGIA E PARTICIPACOES LTDA visa estabelecer dire... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.826** | A.8.26 Requisitos de Segurança em Aplicações | `In Progress` | 4 | CIO / Resp. Segurança | Requisitos de segurança formalizados em tickets Git e validados pelo CTO (POL-APP-001).... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.827** | A.8.27 Arquitetura de Sistemas Segura e Princípios de Engenharia | `In Progress` | 3 | CIO / Resp. Segurança | Princípios de Zero Trust e desacoplamento sensível descritos no SOP-ARC-001.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.828** | A.8.28 Codificação Segura | `In Progress` | 4 | CIO / Resp. Segurança | ## Objetivo A política de segurança da informação para o controle A.8.28 da TWYN T4ISB DO BRASIL TECNOLOGIA E PARTICIPACOES LTDA visa garantir a prote... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.829** | A.8.29 Testes de Segurança em Desenvolvimento e Aceitação | `Implemented` | 4 | CIO / Resp. Segurança | Security testing in SDLC.... |
| **A.830** | A.8.30 Desenvolvimento Terceirizado | `Not Applicable` | 0 | CIO / Resp. Segurança | Outsourced development relationships identified.... |
| **A.831** | A.8.31 Separação dos Ambientes de Desenvolvimento, Teste e Produção | `In Progress` | 4 | CIO / Resp. Segurança | Ambientes de desenvolvimento, homologação e produção segregados logicamente em contas AWS independentes.... (Aprovado por CEO Kacio Giuliano Lopes) |
| **A.832** | A.8.32 Gestão de Mudanças | `In Progress` | 4 | CIO / Resp. Segurança | Change management is universal.... |
| **A.833** | A.8.33 Informação de Teste | `Implemented` | 0 | CIO / Resp. Segurança | Test data protection for development activities.... — ENG-2026-001: SGP-TST-001 (A.8.33) — informação de teste; **aplicável** (há dev/homolog) |
| **A.834** | A.8.34 Proteção dos Sistemas de Informação durante Testes de Auditoria | `Implemented` | 0 | CIO / Resp. Segurança | Audit testing safeguards are universal.... — ENG-2026-001: SGP-AUD-001 (A.8.34) — proteção durante auditoria |

---

## Inconsistências sinalizadas para reconciliação (ENG-2026-001) — ✅ RESOLVIDAS (2026-08-26)

> **Reconciliadas contra o nISO.** Os status abaixo já foram **regenerados a partir da fonte da
> verdade** na tabela acima — esta seção fica como **registro histórico** do que foi sinalizado.
> Exemplos do desfecho: A.6.3 → `Implemented` (EVICERT); A.5.30/A.8.13 → `In Progress`; A.5.25/A.5.28
> → `Implemented` no nISO; os "Implemented" sem lastro (A.8.11/A.8.15/A.8.16/A.8.23) voltaram a
> `Missing`/`In Progress` conforme o nISO. Não constituem parecer de conformidade.

**Tipo A — `Missing` porém com maturidade ≥ 3 e evidência/aprovação (status × evidência):**

| Controle | Status atual | Maturidade | Sinal |
|---|---|---:|---|
| A.6.3 Conscientização/Treinamento | `Missing` | 4 | evidência/aprovação presente sob status `Missing` |
| A.5.17 Informações de Autenticação | `Missing` | 3 | idem |
| A.5.21 Cadeia de Suprimentos TIC | `Missing` | 3 | idem |
| A.5.22 Monitoramento de Fornecedores | `Missing` | 3 | idem |
| A.5.26 Resposta a Incidentes | `Missing` | 3 | idem |
| A.5.30 Prontidão TIC p/ Continuidade | `Missing` | 4 | BCP descrito e aprovado sob status `Missing` |
| A.8.9 Gestão de Configuração | `Missing` | 3 | SOP-HDN-001 citado e aprovado |
| A.8.12 Prevenção de Vazamento (DLP) | `Missing` | 4 | evidência presente |
| A.8.13 Backup da Informação | `Missing` | 4 | "AWS Backup configurado… validado… aprovado" |

**Tipo B — `Implemented` porém com maturidade 0 (status × maturidade):**

| Controle | Status atual | Maturidade | Sinal |
|---|---|---:|---|
| A.6.1 Seleção de Pessoas | `Implemented` | 0 | maturidade 0 sob `Implemented` |
| A.6.2 Termos de Contratação | `Implemented` | 0 | idem |
| A.6.4 Processo Disciplinar | `Implemented` | 0 | idem |
| A.6.8 Notificação de Eventos | `Implemented` | 0 | idem |
| A.5.31 Requisitos Legais | `Implemented` | 0 | idem |

**Ação requerida:** para cada linha, reconciliar contra o nISO e (a) corrigir o status com base
em evidência objetiva, ou (b) rebaixar/abrir o controle. Nenhuma correção de status foi presumida.

---

## Homologação e Assinaturas

Este documento é gerado e validado eletronicamente contra o repositório de produção do nISO.

*   **Responsável pela Segurança da Informação (função):** a ISO/IEC 27001 (cláusula 5.3 / A.5.2) **não exige um cargo intitulado "CISO"** — exige que as responsabilidades de segurança estejam **atribuídas**. Na TWYN, essa função é **atribuída ao cargo de Humberto Oliveira (CIO / Líder de Operações de Segurança)**, conforme roster de governança. _A assinatura anteriormente atribuída a Ricardo Esper foi retirada: Ricardo atua exclusivamente como consultor externo (Aegis), sem papel executivo. Homologação da SoA pelo responsável de segurança **pendente de assinatura**._
*   **Encarregado (DPO):** Bekaa Tecnologia Ltda (PJ) — homologação da SoA **pendente de assinatura** (ref. GOV-DPO-001).
*   **Aprovador Executivo (CEO):** Kacio Giuliano Lopes (Assinado eletronicamente via nISO em 2026-07-27)
