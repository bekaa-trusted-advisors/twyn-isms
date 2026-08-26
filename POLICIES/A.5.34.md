# POL-DPP-001: Política de Proteção de Dados e Privacidade — TWYN Face ID Platform
**ISO/IEC 27001:2022 Controle A.5.34 (Privacidade e proteção de dados pessoais) | ISO/IEC 27701:2025**

---

**Controle de Documento**

| Campo | Valor |
|-------|-------|
| **Document ID** | POL-DPP-001 |
| **Version** | 1.1 (Oficial) |
| **Autor** | Ricardo Esper (Consultor) |
| **Aprovador** | Kacio Giuliano Lopes (CEO) |
| **Data de Emissão** | 16/07/2026 |
| **Status** | Aprovado |

---

## 1. Objetivo

Estabelecer as diretrizes para a proteção de Dados Pessoais Sensíveis Biométricos e salvaguardas de privacidade no processamento da API da TWYN, sob a égide da Lei Geral de Proteção de Dados (LGPD).

---

## 2. Tratamento de Dados Biométricos (Face ID)

A TWYN adota salvaguardas lógicas rígidas para o processamento de imagens e templates faciais:
1.  **Pseudoanonimização:** A TWYN não coleta ou armazena dados cadastrais diretos dos titulares (como Nome, CPF ou RG) vinculados a templates faciais. O vetor biométrico de face (template) é gerado na forma de hash matemático irreversível associado a um ID interno pseudoanônimo.
2.  **Volatilidade Rígida e Expurgo Instantâneo:** As fotos cruas da face coletadas para verificação de vivacidade (liveness check) são processadas exclusivamente em memória RAM e **eliminadas permanentemente em tempo real (0 segundos)** imediatamente após a extração dos vetores biométricos matemáticos. Não há escrita em disco ou buckets de imagens fotográficas brutas.
3.  **Bases Legais e Papel de Privacidade:** Conforme Parecer Jurídico Machado Meyer (Ref 116764899), a TWYN atua na qualidade de **Controladora Independente (Independent Controller)** do algoritmo e infraestrutura de biometria. A base legal legitimadora aplicável ao tratamento de dados biométricos sensíveis sob controle da TWYN é a Prevenção à Fraude e Garantia da Segurança do Titular (LGPD Art. 11, II, "g").

---

## 3. Gestão de Direitos dos Titulares e Protocolo de Exceção (LGPD Art. 18 & Art. 11, II, "g")

1.  O Encarregado (DPO), Bekaa Tecnologia Ltda (PJ), é designado como encarregado exclusivo (`dpo@twyn.com`) para receber e processar demandas de direitos dos titulares (LGPD Art. 18).
2.  **Protocolo de Atendimento a Solicitações de Exclusão (DSAR):**
    *   Quando um titular solicitar a exclusão de seus vetores biométricos (Art. 18, VI), o DPO avaliará se os registros estão vinculados a investigações de fraude ativas ou retenção obrigatória de segurança.
    *   Caso a exclusão seja aplicável, a Engenharia efetuará a remoção definitiva do vetor em até **15 dias úteis**, gerando o hash de auditoria da instrução `DELETE`.
    *   Caso a solicitação atinja registros cuja conservação é estritamente necessária para a garantia da prevenção à fraude no ecossistema (Art. 11, II, "g"), o DPO responderá formalmente ao titular fundamentando a impossibilidade técnica de reconstituição da fotografia original a partir do vetor numérico e indicando a exceção legal legítima.

---

## 4. Revisão e Aprovação

Esta política é aprovada pela Diretoria Executiva da TWYN e revisada anualmente.

**Kacio Giuliano Lopes**  
CEO / Patrocinador Executivo  
TWYN T4ISB DO BRASIL TECNOLOGIA E PARTICIPACOES LTDA (CNPJ: 31.122.819/0001-55)
*Assinado eletronicamente via TWYN GRC Portal em 21/07/2026 18:00 BRT (IP: 189.122.34.55, Hash: 8bce0ce66571d2efc756085370c77358)*
