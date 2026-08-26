# SGP-ADM-001 — Governança de Decisões Automatizadas (Biometria)
**ISO/IEC 27701:2025 Anexo A — A.1.3.11 (Governança de decisões automatizadas) | LGPD Art. 20 (revisão de decisões automatizadas)**

---

**Controle de Documento**

| Campo | Valor |
|---|---|
| **Document ID** | SGP-ADM-001 |
| **Versão** | 1.0 (Rascunho) |
| **Elaborado por** | Consultoria Aegis (ENG-2026-001) |
| **A ser aprovado por** | Encarregado (DPO — Bekaa Tecnologia Ltda) · Humberto Oliveira (CIO) · Kacio Giuliano Lopes (CEO) |
| **Status** | `Rascunho — pendente de aprovação` |

---

## 1. Objetivo

Definir o enquadramento e a governança das **decisões automatizadas** relacionadas ao tratamento
biométrico da TWYN Face ID Platform, assegurando os direitos dos titulares (LGPD Art. 20) e a
transparência exigida pela ISO/IEC 27701:2025 (A.1.3.11).

## 2. Enquadramento de papéis

1. A TWYN, como **Controladora Independente** do algoritmo/infraestrutura de biometria, **fornece o
   resultado da verificação** (booleano de correspondência + score de similaridade) ao cliente
   corporativo (B2B).
2. A **decisão que produz efeitos ao titular** (ex.: aprovar/negar um cadastro, uma transação ou um
   acesso) é tomada pelo **cliente-parceiro B2B** (controlador da relação com o titular final), que
   define suas próprias regras de negócio e limiares de aceitação.
3. A TWYN **não** toma, de forma isolada e unicamente automatizada, decisão com efeito jurídico ou
   impacto significativo sobre o titular final; sua atuação limita-se ao **resultado técnico de
   verificação**.

## 3. Direito de revisão e informação (LGPD Art. 20)

1. O titular pode solicitar informações sobre o tratamento e a **revisão** de decisões automatizadas
   pelo canal do Encarregado (`dpo@twyn.com`), conforme `SGP-PRO-001` (`A.5.34_Rights`).
2. Quando a solicitação disser respeito à **decisão de negócio** (aprovação/negação), o Encarregado
   encaminha e **orienta o titular** quanto ao controlador-parceiro responsável por aquela decisão,
   prestando as informações que couberem à TWYN sobre o resultado técnico fornecido.
3. A TWYN mantém a possibilidade de **reprocessamento técnico** (nova captura/verificação) quando o
   caso indicar erro de correspondência (ver `SGP-DQ-001`).

## 4. Transparência

O aviso de privacidade (`A.5.34_Notice` — SGP-NOTICE-001) informa, em linguagem acessível, a
existência do tratamento biométrico, sua finalidade (prevenção à fraude/autenticação) e a natureza do
resultado fornecido, bem como o canal do Encarregado para exercício de direitos.

## 5. Aprovação

Documento em rascunho — pendente de aprovação. Nenhuma assinatura foi aposta por terceiros.

Aprovação: ______________________________  Data: ____ / ____ / ______
