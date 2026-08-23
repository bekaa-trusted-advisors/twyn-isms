# SGP-DQ-001 — Procedimento de Exatidão e Qualidade de Dados Pessoais (Biometria)
**ISO/IEC 27701:2025 Anexo A — A.1.4.4 (Exatidão e qualidade dos dados pessoais) | LGPD Art. 6º, V (qualidade dos dados)**

---

**Controle de Documento**

| Campo | Valor |
|---|---|
| **Document ID** | SGP-DQ-001 |
| **Versão** | 1.0 (Rascunho) |
| **Elaborado por** | Consultoria Aegis (ENG-2026-001) |
| **A ser aprovado por** | Humberto Oliveira (CIO / Resp. Segurança) · Kacio Lopes (CEO) |
| **Status** | `Rascunho — pendente de aprovação` |

---

## 1. Objetivo

Estabelecer os mecanismos que asseguram a **exatidão, integridade e qualidade** dos dados pessoais
sensíveis (vetores biométricos faciais) tratados pela TWYN Face ID Platform, na medida necessária à
finalidade de identificação, autenticação e prevenção à fraude (LGPD Art. 6º, V; Art. 11, II, 'g').

## 2. Mecanismos de qualidade na captura e extração

1. **Detecção de vivacidade (liveness):** a captura é submetida a verificação de vivacidade para
   rejeitar apresentações fraudulentas (fotos, vídeos, máscaras) antes da extração do vetor.
2. **Qualidade mínima de imagem:** capturas fora de parâmetros (iluminação, enquadramento, resolução,
   oclusão) são rejeitadas na API, evitando a geração de vetores de baixa qualidade.
3. **Extração determinística:** o vetor biométrico é gerado por algoritmo unidirecional; a mesma face,
   dentro dos parâmetros de qualidade, produz representações comparáveis de forma estável.

## 3. Exatidão na verificação (score de similaridade)

1. A verificação retorna **decisão booleana + score de similaridade** contra um limiar (threshold)
   definido e versionado.
2. **Tratamento de erro:** as taxas de **falso-positivo (FMR)** e **falso-negativo (FNMR)** são
   monitoradas; ajustes de limiar são controlados por versão e registrados.
3. Casos limítrofes/rejeições podem ser reprocessados mediante nova captura, sem persistência de
   imagem bruta (expurgo em RAM, 0s — ver `POL-GOV-001` e `ROPA.md`).

## 4. Correção e atualização a pedido do titular

1. O titular pode solicitar correção/atualização de seus dados pelo canal do Encarregado
   (`dpo@twyn.com`), conforme o procedimento de direitos `SGP-PRO-001` (`A.5.34_Rights`).
2. Como o dado tratado é um **vetor irreversível** (não uma ficha cadastral), a "correção" se opera
   pela **regeneração do vetor** a partir de nova captura válida ou pela **exclusão** do vetor
   desatualizado, conforme o caso.

## 5. Aprovação

Documento em rascunho — pendente de aprovação. Nenhuma assinatura foi aposta por terceiros.

Aprovação: ______________________________  Data: ____ / ____ / ______
