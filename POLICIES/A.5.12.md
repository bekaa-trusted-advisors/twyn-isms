# POL-GOV-001: Política de Governança de Dados — TWYN

**ISO/IEC 27001:2022 Controles A.5.12 (Classificação da informação), A.5.13 (Rotulagem da informação), A.5.33 (Proteção de registros) e A.8.10 (Exclusão da informação) | ISO/IEC 27701:2025 Anexo A: A.3.5 (Classificação), A.3.6 (Rotulagem), A.3.14 (Proteção de registros) e A.1.4.6/A.1.4.9 (desidentificação/descarte)**

---

**Controle de Documento**

| Campo | Valor |
|-------|-------|
| **Document ID** | POL-GOV-001 |
| **Version** | 1.0 (Oficial) |
| **Elaborado por** | Ricardo Esper (Consultor) |
| **Aprovado por** | Kacio Giuliano Lopes (CEO) |
| **Data de Emissão** | 21/07/2026 |
| **Status** | Aprovado |

---

## 1. Objetivo e Classes de Informação (A.5.12)

Esta política regula a governança de dados da TWYN, garantindo o manuseio lícito, a integridade e a conformidade perante a LGPD e as normas ISO 27001/27701. Todos os ativos de informação são classificados em quatro níveis:

*   **Restrita (Dados Pessoais Sensíveis / Biometria):** Imagens faciais e vetores/hashes biométricos. Sua exposição causa danos severos e irreparáveis à privacidade.
*   **Confidencial:** Informações estratégicas internas (código-fonte, contratos B2B, chaves criptográficas KMS, segredos comerciais).
*   **Uso Interno:** Informações operacionais comuns (logs operacionais sem PII, organogramas sem CPFs, relatórios internos).
*   **Pública:** Documentações públicas da API, avisos externos de privacidade, termos de uso corporativos.

---

## 2. Regras de Rotulagem da Informação (A.5.13)

1.  **Rotulagem de Bancos de Dados:** Tabelas que contêm hashes biométricos devem possuir metadados rotulados como `[Restrita - Biometric Data]`.
2.  **Repositórios Git:** Os repositórios da TWYN que guardam o código-fonte da API Face ID devem possuir metadados identificadores de confidencialidade como `[Confidencial]`.
3.  **Documentação Digital:** Todos os relatórios do SGSI/SGPI e políticas markdown devem conter cabeçalhos indicando claramente o código do documento e a versão.

---

## 3. Diretrizes de Retenção de Dados (A.5.33)

Todos os dados tratados pela **TWYN Face ID Platform** possuem prazos específicos de retenção para cumprir finalidades legítimas ou obrigações regulatórias:

### Tabela de Temporalidade e Retenção:

| Categoria do Dado | Período de Retenção | Justificativa / Base Legal | Local de Armazenamento |
|---|---|---|---|
| **Imagens Faciais Cruas (Fotos)** | **Instantâneo (0 segundos)** | Minimização extrema e irreversibilidade biométrica (Parecer Machado Meyer Ref 116764899 / LGPD Art. 11). Expurgo em memória RAM imediatamente pós-extração do vetor. | Memória RAM temporária e volátil do microsserviço (sem gravação em disco ou buckets). |
| **Hashes Biométricos** | Indeterminado (enquanto ativo) | Prevenção à Fraude e Segurança do Titular (Art. 11, II, "g" da LGPD). | RDS Aurora AWS (Criptografado AES-256). |
| **Contratos B2B e Fiscais** | **5 anos** após o término | Cumprimento de obrigação legal e prescrição cível. | Repositório físico/digital corporativo seguro. |
| **Documentos de RH e Folha** | **10 anos** | Cumprimento de obrigações previdenciárias e trabalhistas. | Pasta do time de RH sob a gestão da COO Rosa Correia. |
| **Logs de Transação da API** | **12 meses** | Obrigação legal (Marco Civil da Internet, Art. 15). Fica **estritamente vedado** o log de payloads Base64 contendo imagens brutas. | AWS CloudWatch / S3 Glacier (Criptografados). |
| **Backups do Banco de Dados** | **30 dias** | Recuperação de desastres e continuidade do negócio. | AWS Backup Engine. |

---

## 4. Processo de Expurgo e Descarte Seguro (A.8.10)

Quando o prazo de retenção expira ou é solicitada exclusão legal válida pelo DPO:

1.  **Descarte de Imagens (RAM):** Sobrescritas eletronicamente e desalocadas da memória volátil imediatamente (instantâneo / 0 segundos) após a extração dos vetores biométricos unidirecionais.
2.  **Exclusão Biométrica (RDS):** Remoção física dos vetores via instrução SQL `DELETE` com exclusão lógica de registros de índice associados.
3.  **Controle de Logs (A.8.15):** Filtros ativos nos agentes de log (CloudWatch/DataDog) garantem a sanitização automática de qualquer parâmetro temporário de imagem.
4.  **Descarte de Ativos Físicos:** Notebooks descartados devem sofrer sanitização de mídia (cripto-expurgo ou destruição física de discos SSD).

---

## 5. Homologação

**Kacio Giuliano Lopes**  
CEO / Patrocinador Executivo  
TWYN T4ISB DO BRASIL TECNOLOGIA E PARTICIPACOES LTDA (CNPJ: 31.122.819/0001-55)
*Assinado eletronicamente via TWYN GRC Portal em 21/07/2026 18:00 BRT (IP: 189.122.34.55, Hash: bfa14ae9a22e6fc246f6458f73710175)*
