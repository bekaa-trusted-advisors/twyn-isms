# SGP-PRO-001: Procedimento de Atendimento aos Direitos dos Titulares — TWYN
**ISO/IEC 27701:2019 Cláusula 7.3 (Obrigações para com titulares de PII) & LGPD Artigo 18**

---

**Controle de Documento**

| Campo | Valor |
|-------|-------|
| **Document ID** | SGP-PRO-001 |
| **Version** | 1.0 (Oficial) |
| **Elaborado por** | Ricardo Esper (DPO) |
| **Aprovado por** | Rosa Correia (COO / Operações) |
| **Data de Emissão** | 20/07/2026 |
| **Status** | Aprovado |

---

## 1. Canais de Atendimento

Qualquer titular de dados pessoais processados no escopo da TWYN Face ID Platform pode exercer seus direitos através do canal oficial de privacidade gerenciado pelo DPO:
*   **E-mail de Contato:** `dpo@twyn.com.br` (Encarregado Ricardo Esper)

---

## 2. Fluxo de Validação de Identidade

Pela natureza pseudoanônima do processamento da TWYN (onde hashes biométricos são gravados associados a IDs lógicos e sem vínculos diretos com o CPF/Nome civil do titular final), o processo de validação de identidade segue duas vias:

### Via A: Solicitação Indireta (Via Cliente B2B)
1.  O titular solicita a exclusão/acesso de seus dados biométricos diretamente perante o cliente B2B (Controlador que originou o cadastro).
2.  O cliente B2B valida a identidade do titular e envia uma requisição formal de deleção para a TWYN informando a chave interna lúdica (Client ID/User ID).
3.  A TWYN realiza a exclusão com base na requisição do co-controlador.

### Via B: Solicitação Direta (Via DPO da TWYN)
1.  O titular entra em contato via e-mail `dpo@twyn.com.br`.
2.  O DPO solicita que o usuário forneça o nome do aplicativo/empresa parceira onde efetuou o cadastro biométrico e o respectivo CPF para cruzamento local pelo co-controlador de origem.
3.  Após a validação bem-sucedida da legitimidade da identidade, o DPO emite o ticket interno.

---

## 3. Prazos e Execução Técnica da Exclusão

1.  **Prazo Legal:** A exclusão dos dados ou a confirmação de tratamento deve ser respondida no prazo máximo de **15 dias** contados da validação de identidade.
2.  **Execução Técnica:** O DevOps (Marcelo Mascarenhas) executa a query de deleção lógica e física no banco RDS Aurora a partir do ID confirmado.
3.  **Registro de Auditoria:** Um log criptográfico comprovando a deleção física (contendo apenas o timestamp e o ID excluído, sem os pontos do hash anterior) é gravado no repositório de logbooks de auditoria para fins de conformidade perante a ANPD.

---

## 4. Revisão e Homologação

**Rosa Correia**  
COO / Operações  
TWYN T4ISB DO BRASIL TECNOLOGIA E PARTICIPACOES LTDA (CNPJ: 31.122.819/0001-55)
*Assinado eletronicamente via TWYN GRC Portal em 21/07/2026 18:00 BRT (IP: 187.12.89.201, Hash: 6e19728ec00c00ef1af5cea10d2f9b2f)*
