# POL-LEG-002 - Minuta Padrão de Co-Controladoria Independente e Aditivo de Tratamento de Dados (DPA B2B)

**Código:** POL-LEG-002  
**Versão:** 1.0  
**Data de Aprovação:** 22/07/2026  
**Classificação:** Uso Interno e Clientes B2B  
**Aprovadores:** Humberto Oliveira (CPO) / Kacio Lopes (CEO) / Ricardo Esper (DPO)  

---

## 1. Objetivo e Âmbito de Aplicação

Esta política e minuta padrão regulam os termos contratuais de Proteção de Dados e Co-Controladoria Independente aplicáveis a todas as integrações comerciais da **TWYN Face ID Platform** com clientes corporativos (B2B), em estrita observância à Lei Geral de Proteção de Dados (LGPD - Lei nº 13.709/2018), às normas ISO/IEC 27001:2022 e ISO/IEC 27701:2019, e ao **Parecer Jurídico Especializado Machado Meyer (Ref. 116764899)**.

---

## 2. Enquadramento de Controladoria Independente

Conforme análise jurídica conclusiva do Parecer Machado Meyer:

1. **Autonomia Tecnológica:** A TWYN atua como **Controladora Independente** dos dados pessoais sensíveis biométricos por ela processados, uma vez que detém a propriedade intelectual, os parâmetros do algoritmo de inteligência artificial, o modelo de extração de características e a infraestrutura de vetorização biométrica.
2. **Base Legal Primária:** O tratamento de dados biométricos faciais pela TWYN fundamenta-se expressamente no **Art. 11, inciso II, alínea "g" da LGPD** (*garantia da prevenção à fraude e à segurança do titular nos processos de identificação e autenticação de cadastro em sistemas eletrônicos*).
3. **Ausência de Subordinação Operacional:** A TWYN não atua como mera operadora subordinada, possuindo responsabilidade direta perante a Autoridade Nacional de Proteção de Dados (ANPD) e os titulares de dados no tocante à integridade e segurança do ambiente de vetorização.

---

## 3. Cláusulas Obrigatórias da Minuta DPA/ICA B2B

Todos os contratos celebrados pela TWYN com parceiros e clientes corporativos que consumam a API Face ID deverão conter os seguintes compromissos:

### Cláusula 3.1 — Minimização e Irreversibilidade Biométrica
A TWYN garante que o processamento biométrico converte imagens faciais em vetores matemáticos unidirecionais de 512 ou 1024 dimensões (hashes biométricos). A imagem fotográfica fotográfica original é **eliminada imediatamente em tempo real pós-extração**, sendo vedado o armazenamento de acervo fotográfico bruto em bancos de dados.

### Cláusula 3.2 — Proteção e Criptografia
A TWYN compromete-se a manter os vetores biométricos criptografados em repouso com algoritmo AES-256 e em trânsito com protocolo TLS 1.3, em ambiente de nuvem isolado (AWS us-east-1), certificado nas normas ISO/IEC 27001 e ISO/IEC 27701.

### Cláusula 3.3 — Notificação de Incidentes de Segurança
Em caso de incidente confirmado que possa acarretar risco ou dano relevante aos titulares ou à infraestrutura de biometria, a TWYN notificará o CLIENTE e a ANPD no prazo máximo de **24 (vinte e quatro) horas** contadas da ciência do evento, prestando as informações necessárias à mitigação de impactos.

### Cláusula 3.4 — Transparência e Exercício de Direitos
Cada Parte compromete-se a manter em seus respectivos canais de atendimento aos titulares (DPO) mecanismos transparentes para o recebimento de requisições de direitos (LGPD Art. 18).

---

## 4. Histórico de Versões e Assinaturas

| Versão | Data | Descrição da Alteração | Autor / Aprovador |
|---|---|---|---|
| 1.0 | 22/07/2026 | Edição inicial baseada no Parecer Machado Meyer Ref 116764899 | Ricardo Esper (DPO) / Kacio Lopes (CEO) |

---
**Assinatura Digital de Aprovação (nISO D1):**  
*Aprovado por Kacio Lopes (CEO) em 22/07/2026 via TWYN GRC Portal.*  
*Hash de Integridade:* `d1-sha256-pol-leg-002-v1.0-machadomeyer-approved`
