# POL-IRP-001: Política de Resposta a Incidentes de SI — TWYN Face ID Platform
**ISO/IEC 27001:2022 Controles A.5.24 (Planejamento e preparação para resposta a incidentes), A.5.25, A.5.26, A.5.27, A.5.28, A.5.5 e A.5.6**

---

**Controle de Documento**

| Campo | Valor |
|-------|-------|
| **Document ID** | POL-IRP-001 |
| **Version** | 1.1 (Oficial) |
| **Autor** | Ricardo Esper (Consultor) |
| **Aprovador** | Kacio Lopes (CEO) |
| **Data de Emissão** | 16/07/2026 |
| **Status** | Aprovado |

---

## 1. Objetivo

Garantir uma resposta coordenada, rápida e eficaz a incidentes de segurança da informação e privacidade na TWYN Face ID Platform, minimizando danos operacionais, regulatórios e de reputação.

---

## 2. Comitê de Resposta a Incidentes (CSIRT)

Fica instituído o Comitê CSIRT permanente da TWYN com os seguintes papéis:
*   **Coordenação Jurídica e de Privacidade (DPO):** Humberto Oliveira (DPO — responsável por coordenação legal, forense de privacidade e notificações à ANPD).
*   **Líder de Operações de Segurança & CIO:** Humberto Oliveira (responsável por triagem inicial de alertas, análise de rede e segurança de acessos).
*   **Líder Técnico de Contenção & DevOps:** Marcelo Mascarenhas (responsável pelo isolamento técnico de instâncias AWS e mitigação lógica).
*   **CTO & CISO:** Nizar Elouaer (responsável por aprovar modificações de código de segurança e conformidade técnica).
*   **Patrocinador Executivo & CEO:** Kacio Lopes (responsável por autorizações críticas de negócios).

---

## 3. Workflow de Resposta a Incidentes (A.5.24, A.5.26)

O CSIRT deve seguir as seguintes 5 etapas lógicas de resposta:
1.  **Triagem e Análise (A.5.25):** Confirmar a ocorrência do incidente, classificar a severidade e registrar no log interno do CSIRT.
    *   *P0/P1 (Crítico/Alto):* Comprometimento de templates biométricos ou vazamento de chaves mestras AWS KMS.
    *   *P2/P3 (Médio/Baixo):* Vulnerabilidades não exploradas ou indisponibilidades temporárias em sandbox.
2.  **Contenção:** Executar bloqueios lógicos imediatos (revogação de acessos via AWS IAM, isolamento de subredes).
3.  **Erradicação:** Identificar e eliminar a causa raiz (remoção de malware, patches em código ou configuração).
4.  **Recuperação e Restabelecimento:** Restaurar os serviços a partir de backups limpos e monitorar estabilidade.
5.  **Pós-Mortem e Aprendizado (A.5.27):** Elaborar relatório detalhado de lições aprendidas em até 5 dias úteis, atualizando controles do SGSI para prevenir recorrência.

---

## 4. Coleta de Evidências Forenses (A.5.28)

Para qualquer incidente classificado como P0/P1:
1.  **Preservação de Logs:** O DevOps (Marcelo Mascarenhas) deve congelar os logs de auditoria correspondentes (CloudTrail, VPC Flow Logs, Application logs) e salvá-los em bucket S3 criptografado e isolado com retenção de 1 ano.
2.  **Cadeia de Custódia:** Toda evidência coletada deve possuir o seu hash (SHA-256) registrado no log do incidente para garantir a integridade em eventuais processos legais.

---

## 5. Relações com Autoridades e Grupos de Interesse (A.5.5, A.5.6)

1.  **Notificação ANPD (A.5.5):** Em incidentes envolvendo PII biométrica que representem risco para os direitos dos titulares, o DPO Humberto Oliveira deve notificar a ANPD em até **2 dias úteis** da ciência do fato.
2.  **Grupos de Interesse (A.5.6):** Enviar relatórios de inteligência de ameaças ao **CERT.br** e colaborar ativamente com fóruns de privacidade (ANPPD).

---

## 6. Revisão e Aprovação

Esta política é aprovada pela Diretoria Executiva da TWYN e revisada anualmente.

**Kacio Lopes**  
CEO / Patrocinador Executivo  
TWYN T4ISB DO BRASIL TECNOLOGIA E PARTICIPACOES LTDA (CNPJ: 31.122.819/0001-55)
*Assinado eletronicamente via TWYN GRC Portal em 21/07/2026 18:00 BRT (IP: 189.122.34.55, Hash: 7f7d54061cdc5bbc47deb64f087ea9f4)*
