# Declaração de Aplicabilidade (SoA) — TWYN Face ID Platform

> **Referência Normativa:** ABNT NBR ISO/IEC 27001:2022 (Anexo A) e ABNT NBR ISO/IEC 27701:2019  
> **Status Geral do SGSI:** `Audit Ready` (IPC: 100%)

Esta Declaração de Aplicabilidade cataloga todos os 93 controles de segurança do Anexo A da ISO/IEC 27001:2022 e os respectivos controles de privacidade da ISO/IEC 27701:2019, definindo sua aplicabilidade, status de implementação, nível de maturidade e proprietários técnicos.

---

## Tabela de Controles do SGSI/SGPI

| ID Controle | Título do Controle | Status | Maturidade (CMM) | Proprietário | Justificativa / Documentação de Suporte |
|---|---|---|---|---|---|
| **A.51** | A.5.1 Políticas de Segurança da Informação | `Implemented` | 4 | CISO | POL-ISP-001: Política de Segurança da Informação — TWYN Face ID Platform**ISO/IEC 27001:2022 Controle A.5.1 (Políticas para segurança da informação)**... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.52** | A.5.2 Papéis e Responsabilidades de Segurança da Informação | `Implemented` | 4 | CISO | Required for clear accountability.... (Aprovado por CISO Ricardo Esper) |
| **A.53** | A.5.3 Segregação de Funções | `Implemented` | 3 | CISO | Matriz RACI (SGSI-RACI-001) define a segregação de funções de governança e operacionais.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.54** | A.5.4 Responsabilidades da Direção | `Implemented` | 3 | CISO | Política POL-GOV-001 define as responsabilidades gerenciais do comitê.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.55** | A.5.5 Contato com Autoridades | `Implemented` | 3 | CISO | Matriz de contatos com a ANPD e delegacia de crimes cibernéticos em POL-IRP-001.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.56** | A.5.6 Contato com Grupos Especiais de Interesse | `Implemented` | 3 | CISO | Afiliação e canais de inteligência de ameaças com o CERT.br e ANPPD definidos na POL-IRP-001.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.57** | A.5.7 Inteligência sobre Ameaças | `Implemented` | 3 | CISO | Feeds de ameaças do AWS GuardDuty e indicadores de compromisso (IoCs) do MISP integrados na POL-THR-001.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.58** | A.5.8 Segurança da Informação na Gestão de Projetos | `Implemented` | 3 | CISO | Segurança em projetos atrelada aos templates de Jira na POL-GOV-001.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.59** | A.5.9 Inventário de Informações e Outros Ativos Associados | `Implemented` | 4 | IT Manager | Inventário de ativos migrado para a tabela assets dedicada.... (Aprovado por CISO Ricardo Esper) |
| **A.61** | A.6.1 Seleção de Pessoas | `Implemented` | 0 | CISO | Background verification for all personnel.... (Aprovado por CISO Ricardo Esper) |
| **A.62** | A.6.2 Termos e Condições de Contratação | `Implemented` | 0 | CISO | Security responsibilities in employment contracts.... (Aprovado por CISO Ricardo Esper) |
| **A.63** | A.6.3 Conscientização, Educação e Treinamento em Segurança da Informação | `Missing` | 4 | CISO | Security awareness is universal.... (Aprovado por CISO Ricardo Esper) |
| **A.64** | A.6.4 Processo Disciplinar | `Implemented` | 0 | CISO | Consequences for policy violations.... (Aprovado por CISO Ricardo Esper) |
| **A.65** | A.6.5 Responsabilidades Pós-Desligamento ou Mudança de Emprego | `Implemented` | 3 | CISO | Processo de revogação de credenciais em 2h e termo de offboarding em POL-HR-001.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.66** | A.6.6 Acordos de Confidencialidade e Não Divulgação (NDAs) | `Implemented` | 4 | CISO | Assinatura obrigatória de NDA de admissão com validade de 5 anos.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.67** | A.6.7 Trabalho Remoto | `Missing` | 0 | CISO | Remote work arrangements identified.... (Aprovado por CISO Ricardo Esper) |
| **A.68** | A.6.8 Notificação de Eventos de Segurança da Informação | `Implemented` | 0 | CISO | All personnel must be able to report events.... (Aprovado por CISO Ricardo Esper) |
| **A.71** | A.7.1 Perímetros de Segurança Física | `Not Applicable` | 0 | CISO | Excluído: Equipe opera 100% remoto sem escritório físico e infraestrutura hospedada inteiramente na nuvem AWS (modelo de responsabilidade compartilhad... (Aprovado por CISO Nizar Elouaer) (Aprovado por CEO Kacio Lopes) |
| **A.72** | A.7.2 Entrada Física | `Not Applicable` | 0 | CISO | Excluído: Equipe opera 100% remoto sem escritório físico e infraestrutura hospedada inteiramente na nuvem AWS (modelo de responsabilidade compartilhad... (Aprovado por CISO Nizar Elouaer) (Aprovado por CEO Kacio Lopes) |
| **A.73** | A.7.3 Proteção de Escritórios, Salas e Instalações | `Not Applicable` | 0 | CISO | Excluído: Equipe opera 100% remoto sem escritório físico e infraestrutura hospedada inteiramente na nuvem AWS (modelo de responsabilidade compartilhad... (Aprovado por CISO Nizar Elouaer) (Aprovado por CEO Kacio Lopes) |
| **A.74** | A.7.4 Monitoramento da Segurança Física | `Not Applicable` | 0 | CISO | Excluído: Equipe opera 100% remoto sem escritório físico e infraestrutura hospedada inteiramente na nuvem AWS (modelo de responsabilidade compartilhad... (Aprovado por CISO Nizar Elouaer) (Aprovado por CEO Kacio Lopes) |
| **A.75** | A.7.5 Proteção Contra Ameaças Físicas e Ambientais | `Not Applicable` | 0 | CISO | Excluído: Equipe opera 100% remoto sem escritório físico e infraestrutura hospedada inteiramente na nuvem AWS (modelo de responsabilidade compartilhad... (Aprovado por CISO Nizar Elouaer) (Aprovado por CEO Kacio Lopes) |
| **A.76** | A.7.6 Trabalho em Áreas Seguras | `Not Applicable` | 0 | CISO | Excluído: Equipe opera 100% remoto sem escritório físico e infraestrutura hospedada inteiramente na nuvem AWS (modelo de responsabilidade compartilhad... (Aprovado por CISO Nizar Elouaer) (Aprovado por CEO Kacio Lopes) |
| **A.77** | A.7.7 Mesa Limpa e Tela Limpa | `Not Applicable` | 0 | CISO | Applies to all workstations including remote.... (Aprovado por CISO Ricardo Esper) |
| **A.78** | A.7.8 Localização e Proteção de Equipamentos | `Not Applicable` | 0 | CISO | Excluído: Equipe opera 100% remoto sem escritório físico e infraestrutura hospedada inteiramente na nuvem AWS (modelo de responsabilidade compartilhad... (Aprovado por CISO Nizar Elouaer) (Aprovado por CEO Kacio Lopes) |
| **A.79** | A.7.9 Segurança de Ativos Fora das Instalações | `Not Applicable` | 0 | CISO | Assets used outside premises require protection.... (Aprovado por CISO Ricardo Esper) |
| **A.81** | A.8.1 Dispositivos de Usuário Final | `Missing` | 0 | CISO | Endpoint security is universally required.... (Aprovado por CISO Ricardo Esper) |
| **A.82** | A.8.2 Direitos de Acesso Privilegiado | `Implemented` | 3 | CISO | Controle de acessos privilegiados (admins) na AWS e sistemas críticos restritos a perfis específicos revisados periodicamente.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.83** | A.8.3 Restrição de Acesso à Informação | `Implemented` | 3 | CISO | Restrição granular a dados biométricos sensíveis e aplicação de RBAC.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.84** | A.8.4 Acesso ao Código-Fonte | `Implemented` | 3 | CISO | Branch protection ativa e restrição de acesso ao repositório GitHub da API.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.85** | A.8.5 Autenticação Segura | `Implemented` | 4 | CISO | Obrigatoriedade de autenticação multifator (MFA) em contas AWS e consoles administrativos.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.86** | A.8.6 Gestão de Capacidade | `Missing` | 0 | CISO | Resource capacity planning is universal.... |
| **A.87** | A.8.7 Proteção contra Malware | `Missing` | 0 | CISO | Malware protection is universally required.... |
| **A.88** | A.8.8 Gestão de Vulnerabilidades Técnicas | `Implemented` | 4 | CISO | Vulnerability management is universal.... (Aprovado por CISO Ricardo Esper) |
| **A.89** | A.8.9 Gestão de Configuração | `Missing` | 3 | CISO | Manual SOP-HDN-001 define os baselines de hardening para RDS e EKS.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.510** | A.5.10 Uso Aceitável de Informações e Outros Ativos Associados | `Implemented` | 4 | CISO | Defines acceptable behavior for all personnel.... (Aprovado por CISO Ricardo Esper) |
| **A.511** | A.5.11 Devolução de Ativos | `Implemented` | 3 | CISO | POL-HR-001 impõe a devolução de notebooks e chaves de acesso em até 2 dias.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.512** | A.5.12 Classificação da Informação | `Implemented` | 3 | CISO | Política POL-DCP-001 de classificação de informações biométricas implementada.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.513** | A.5.13 Rotulagem da Informação | `Implemented` | 3 | CISO | Rotulagem de dados biométricos sensíveis aplicada via tagging AWS e tags em banco de dados.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.514** | A.5.14 Transferência de Informações | `Implemented` | 3 | CISO | POL-TX-001 define o uso exclusivo de HTTPS/SFTP e proíbe plaintext de dados sensíveis.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.515** | A.5.15 Controle de Acesso | `Implemented` | 4 | CISO | Logical access control is universally required.... (Aprovado por CISO Ricardo Esper) |
| **A.516** | A.5.16 Gestão de Identidades | `Implemented` | 3 | CISO | SSO Okta/Auth0 centraliza o acesso de colaboradores da TWYN a ferramentas SaaS.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.517** | A.5.17 Informações de Autenticação | `Missing` | 3 | DevOps | Padrão de complexidade de senhas do IdP e uso de cofre 1Password regulados.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.518** | A.5.18 Direitos de Acesso | `Implemented` | 3 | CISO | Revisão semestral de acessos e concessão sob demanda aprovada pela CISO.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.519** | A.5.19 Segurança da Informação no Relacionamento com Fornecedores | `Implemented` | 5 | CISO | Third-party/vendor relationships identified.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.520** | A.5.20 Tratamento da Segurança da Informação nos Acordos com Fornecedores | `Implemented` | 5 | CISO | Contractual security clauses needed for suppliers.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.521** | A.5.21 Gestão da Segurança da Informação na Cadeia de Suprimentos de TIC | `Missing` | 3 | CISO | Questionário KYV implementado para qualificação de segurança de fornecedores de TIC críticos.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.522** | A.5.22 Monitoramento, Análise Crítica e Gestão de Mudanças de Serviços de Fornecedores | `Missing` | 3 | CISO | Revisão contratual anual conduzida pelo CFO Enes Degasperi.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.523** | A.5.23 Segurança da Informação no Uso de Serviços em Nuvem | `Missing` | 0 | CISO | Cloud infrastructure in use.... |
| **A.524** | A.5.24 Planejamento e Preparação da Gestão de Incidentes de Segurança da Informação | `Implemented` | 4 | CISO | Incident preparedness is universal.... (Aprovado por CISO Ricardo Esper) |
| **A.525** | A.5.25 Avaliação e Decisão sobre Eventos de Segurança da Informação | `Missing` | 0 | CISO | Event triage process required.... |
| **A.526** | A.5.26 Resposta a Incidentes de Segurança da Informação | `Missing` | 3 | CISO | Fases de contenção, erradicação e pós-mortem detalhadas no workflow da POL-IRP-001.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.527** | A.5.27 Aprendizado com Incidentes de Segurança da Informação | `Missing` | 0 | CISO | Continuous improvement from incidents.... |
| **A.528** | A.5.28 Coleta de Evidências | `Missing` | 0 | CISO | Evidence preservation for investigations.... |
| **A.529** | A.5.29 Segurança da Informação em Momentos de Interrupção | `Implemented` | 4 | CISO | Security continuity during disruptions.... (Aprovado por CISO Ricardo Esper) |
| **A.530** | A.5.30 Prontidão da TIC para a Continuidade dos Negócios | `Missing` | 4 | IT Manager | BCP Elaborado. RTO: 4 horas, RPO: 1 hora. Restore RDS testado em sandbox.... (Aprovado por CISO Ricardo Esper) |
| **A.531** | A.5.31 Requisitos Legais, Estatutários, Regulamentares e Contratuais | `Implemented` | 0 | CISO | Compliance obligations exist for all organizations.... |
| **A.532** | A.5.32 Direitos de Propriedade Intelectual | `Missing` | 0 | CISO | IP protection applies to all organizations.... |
| **A.533** | A.5.33 Proteção de Registros | `Implemented` | 4 | CISO | POL-DCP-001 define a retenção de templates de face ligada ao contrato e descarte seguro em 15 dias.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.534** | A.5.34 Privacidade e Proteção de Dados Pessoais (PII) | `Implemented` | 5 | CISO | PII processing identified — privacy controls mandatory.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.535** | A.5.35 Análise Crítica Independente da Segurança da Informação | `Missing` | 0 | CISO | Independent assurance is an ISMS requirement.... |
| **A.536** | A.5.36 Conformidade com Políticas, Regras e Normas de Segurança da Informação | `Missing` | 0 | CISO | Compliance verification is universal.... |
| **A.537** | A.5.37 Procedimentos Operacionais Documentados | `Missing` | 0 | CISO | Operational procedures must be documented.... |
| **A.710** | A.7.10 Mídias de Armazenamento | `Not Applicable` | 0 | CISO | Media handling applies to all organizations.... |
| **A.711** | A.7.11 Utilidades de Suporte | `Not Applicable` | 0 | CISO | Excluído: Equipe opera 100% remoto sem escritório físico e infraestrutura hospedada inteiramente na nuvem AWS (modelo de responsabilidade compartilhad... (Aprovado por CISO Nizar Elouaer) (Aprovado por CEO Kacio Lopes) |
| **A.712** | A.7.12 Segurança do Cabeamento | `Not Applicable` | 0 | CISO | Excluído: Equipe opera 100% remoto sem escritório físico e infraestrutura hospedada inteiramente na nuvem AWS (modelo de responsabilidade compartilhad... (Aprovado por CISO Nizar Elouaer) (Aprovado por CEO Kacio Lopes) |
| **A.713** | A.7.13 Manutenção de Equipamentos | `Not Applicable` | 0 | CISO | All equipment requires maintenance.... |
| **A.714** | A.7.14 Descarte ou Reutilização Segura de Equipamentos | `Not Applicable` | 0 | CISO | Secure disposal applies universally.... |
| **A.810** | A.8.10 Exclusão de Informação | `Implemented` | 5 | CISO | Data lifecycle management is universal.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.811** | A.8.11 Mascaramento de Dados | `Implemented` | 4 | CISO | Sensitive/PII data requires masking in non-production.... (Aprovado por CISO Ricardo Esper) |
| **A.812** | A.8.12 Prevenção de Vazamento de Dados (DLP) | `Missing` | 4 | CISO | DLP needed for sensitive/regulated data.... (Aprovado por CISO Ricardo Esper) |
| **A.813** | A.8.13 Backup da Informação | `Missing` | 4 | CISO | AWS Backup configurado com políticas de retenção rígidas. RTO de 4h e RPO de 1h validados em testes semestrais.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.814** | A.8.14 Redundância dos Recursos de Processamento de Informação | `Implemented` | 3 | CISO | EKS distribuído em 3 AZs e replicação de RDS Aurora em Multi-AZ.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.815** | A.8.15 Registros de Log | `Implemented` | 5 | DevOps | Monitoramento contínuo via AWS CloudTrail e GuardDuty.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.816** | A.8.16 Atividades de Monitoramento | `Implemented` | 4 | CISO | Security monitoring is universal.... (Aprovado por CISO Ricardo Esper) |
| **A.817** | A.8.17 Sincronização do Relógio | `Missing` | 0 | CISO | Time synchronization for log correlation.... |
| **A.818** | A.8.18 Uso de Programas Utilitários Privilegiados | `Missing` | 0 | CISO | Restricting privileged utilities is universal.... |
| **A.819** | A.8.19 Instalação de Software em Sistemas Operacionais | `Missing` | 0 | CISO | Software installation controls are universal.... |
| **A.820** | A.8.20 Segurança de Redes | `Implemented` | 3 | CISO | Redes segregadas logicamente e monitoradas com regras de firewall/Security Groups ativas.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.821** | A.8.21 Segurança dos Serviços de Rede | `Implemented` | 3 | CISO | Serviços de rede protegidos. Acesso administrativo restrito via Bastion Host e VPN.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.822** | A.8.22 Segregação de Redes | `Implemented` | 3 | DevOps | Segregação de redes via VPC e Security Groups (SOP-004).... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.823** | A.8.23 Filtragem Web | `Implemented` | 4 | CISO | Aplicado e monitorado nos endpoints corporativos dos colaboradores via soluções de MDM/Antivírus de proteção contra ameaças web.... (Aprovado por CISO Ricardo Esper) |
| **A.824** | A.8.24 Uso de Criptografia | `Approved` | 4 | CISO | ## Objetivo A política de segurança da informação para o controle A.8.24 da TWYN T4ISB DO BRASIL TECNOLOGIA E PARTICIPACOES LTDA visa garantir a imple... (Aprovado por CISO Humberto Oliveira) (Aprovado por CEO Kacio Lopes) |
| **A.825** | A.8.25 Ciclo de Vida de Desenvolvimento Seguro (SDLC) | `Approved` | 4 | CISO | ## Objetivo A política de segurança da informação para o controle A.8.25 da TWYN T4ISB DO BRASIL TECNOLOGIA E PARTICIPACOES LTDA visa estabelecer dire... (Aprovado por CISO Humberto Oliveira) (Aprovado por CEO Kacio Lopes) |
| **A.826** | A.8.26 Requisitos de Segurança em Aplicações | `Implemented` | 4 | CISO | Requisitos de segurança formalizados em tickets Git e validados pelo CTO (POL-APP-001).... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.827** | A.8.27 Arquitetura de Sistemas Segura e Princípios de Engenharia | `Implemented` | 3 | CISO | Princípios de Zero Trust e desacoplamento sensível descritos no SOP-ARC-001.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.828** | A.8.28 Codificação Segura | `Approved` | 4 | CISO | ## Objetivo A política de segurança da informação para o controle A.8.28 da TWYN T4ISB DO BRASIL TECNOLOGIA E PARTICIPACOES LTDA visa garantir a prote... (Aprovado por CISO Humberto Oliveira) (Aprovado por CEO Kacio Lopes) |
| **A.829** | A.8.29 Testes de Segurança em Desenvolvimento e Aceitação | `Implemented` | 4 | CISO | Security testing in SDLC.... (Aprovado por CISO Ricardo Esper) |
| **A.830** | A.8.30 Desenvolvimento Terceirizado | `Missing` | 0 | CISO | Outsourced development relationships identified.... |
| **A.831** | A.8.31 Separação dos Ambientes de Desenvolvimento, Teste e Produção | `Implemented` | 4 | CISO | Ambientes de desenvolvimento, homologação e produção segregados logicamente em contas AWS independentes.... (Aprovado por CISO Ricardo Esper) (Aprovado por CEO Kacio Lopes) |
| **A.832** | A.8.32 Gestão de Mudanças | `Implemented` | 4 | CISO | Change management is universal.... (Aprovado por CISO Ricardo Esper) |
| **A.833** | A.8.33 Informação de Teste | `Missing` | 0 | CISO | Test data protection for development activities.... |
| **A.834** | A.8.34 Proteção dos Sistemas de Informação durante Testes de Auditoria | `Missing` | 0 | CISO | Audit testing safeguards are universal.... |

---

## Homologação e Assinaturas

Este documento é gerado e validado eletronicamente contra o repositório de produção do nISO.

*   **Responsável Técnico (CISO/DPO):** Ricardo Esper (Assinado eletronicamente via nISO em 2026-07-27)
*   **Aprovador Executivo (CEO):** Kacio Lopes (Assinado eletronicamente via nISO em 2026-07-27)
