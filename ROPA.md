# Registro de Operações de Tratamento de Dados Pessoais (ROPA) — TWYN

> **Referência Regulatória:** Artigo 37 da Lei Geral de Proteção de Dados (LGPD - Lei nº 13.709/2018) / ABNT NBR ISO/IEC 27701:2025 (SGPI).

Este documento registra as operações de tratamento de dados pessoais e dados pessoais sensíveis (biometria) executadas no escopo da plataforma **Face ID Platform API** da Twyn.

---

## 📋 Inventário de Fluxos de Tratamento

### Fluxo 1 — Vetorização Biométrica Facial para Autenticação e Prevenção à Fraude

*   **Finalidade Principal:** Identificação, autenticação de identidade e prevenção a fraudes em cadastros e transações eletrônicas de aplicativos parceiros B2B.
*   **Dados Coletados:** Imagem facial (foto estilo "selfie") enviada em formato JPG/PNG via API.
*   **Dados Sensíveis Tratados:** Biometria facial (vetorização matemática).
*   **Categoria de Titulares:** Usuários finais dos clientes B2B que contratam a API da Twyn para verificação cadastral.
*   **Base Legal da LGPD:** **Artigo 11, II, alínea 'g'** (Tratamento de dados sensíveis sem consentimento do titular, quando indispensável para a prevenção à fraude e à segurança do titular nos processos de identificação e autenticação de cadastro em sistemas eletrônicos).
*   **Papel da Organização:** **Controlador Independente** (conforme enquadramento jurídico formal no Parecer Especializado Machado Meyer Ref 116764899 e Termo de Co-Controladoria POL-LEG-002).

---

## 🔒 Ciclo de Vida e Segurança Técnica

1.  **Ingressão do Dado (API):** A imagem facial é enviada por canal seguro HTTPS (criptografia em trânsito TLS 1.3) para a API pública na AWS.
2.  **Processamento e Extração (RAM):** A imagem é carregada diretamente na memória volátil (RAM) do servidor EKS. O algoritmo proprietário extrai os pontos biométricos e gera um vetor numérico unidirecional.
3.  **Expurgo Imediato de Imagem Bruta:** A foto original em formato de arquivo de imagem é apagada da memória RAM do servidor no instante em que o vetor biométrico é gerado (**tempo de descarte: 0 segundos**). Nenhuma imagem facial em formato bruto é gravada em discos permanentes (EBS/S3).
4.  **Armazenamento do Vetor Biométrico:** Apenas o vetor numérico (vetorização matemática irreversível) é gravado no banco de dados AWS RDS de produção.
5.  **Criptografia em Repouso:** Os volumes do banco RDS e logs de aplicação são criptografados em repouso utilizando algoritmos robustos AES-256 via chaves customizadas no AWS KMS.

---

## 🌍 Compartilhamento e Transferência Internacional

*   **Destinatários dos Dados:** Os parceiros B2B solicitantes recebem apenas a resposta booleana de validação (verdadeiro/falso + score de similaridade). Não há compartilhamento dos vetores matemáticos biométricos com nenhum terceiro.
*   **Transferência Internacional de Dados:** Os servidores e bancos de dados de produção estão hospedados no datacenter da AWS na região dos EUA (`us-east-1`).
*   **Mecanismo de Salvaguarda da LGPD:** Esta transferência está amparada contratualmente por cláusulas de privacidade padrão corporativas (Standard Contractual Clauses - SCCs) e no Termo de Diligência de Privacidade (SGP-KYV-001).

---

## 👥 Canal de Atendimento e Direitos dos Titulares

*   **Canal Central de Recebimento de DSAR:** Mensagens de privacidade são recebidas via e-mail centralizador: **`privacy@t4isb.com`**
*   **Procedimento de Exclusão:** As solicitações legítimas de titulares para exclusão de dados biometrizados são tratadas via procedimento específico (SGP-PRO-001) para deletar o registro do ID do vetor matemático no RDS no prazo de até 15 dias.

---

## 📅 Homologação e Revisão

*   **Responsável pela Atualização:** Bekaa Trusted Advisors (Encarregado/DPO — PJ)
*   **Última Revisão:** 2026-07-27
*   **Status de Auditoria:** Conforme / Auditado
