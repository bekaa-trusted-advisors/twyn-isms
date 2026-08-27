# Designação da Auditoria Interna do SGSI/SGPI (ISO/IEC 27001:2022 cl. 9.2) — TWYN

**Referência:** ISO/IEC 27001:2022, cláusula **9.2** (Auditoria interna) · ISO/IEC 27701:2025 · ISO 19011 (diretrizes para auditoria de sistemas de gestão).

---

**Controle de Documento**

| Campo | Valor |
|---|---|
| **Document ID** | GOV-AUD-001 |
| **Versão** | 1.0 |
| **Elaborado por** | Consultoria Aegis (ENG-2026-001) — *instrumento de designação; não é execução da auditoria* |
| **Aprovação / assinatura** | Direção da TWYN (dona do programa de auditoria) + ness (parte executante) |
| **Status** | `Minuta para assinatura — pendente de declaração de imparcialidade e credenciais` |

---

## 1. Partes

| Papel | Entidade |
|---|---|
| **Organização auditada (dona do programa 9.2)** | **TWYN — T4ISB do Brasil Tecnologia e Participações Ltda** (CNPJ 31.122.819/0001-55) |
| **Parte executante da auditoria interna (PJ)** | **ness Processos e Tecnologia Ltda** (CNPJ 72.027.097/0001-37) |
| **Auditora-líder designada** | **Monica Yoshida Barbosa** (credenciais a anexar — item 4) |

> A **execução** da auditoria interna é terceirizada à ness; a **titularidade do programa** (definição
> de escopo, frequência, recebimento do relatório e tratamento de não conformidades) **permanece com a
> direção da TWYN**.

## 2. Base de independência e imparcialidade (o ponto crítico)

A cláusula 9.2.2 exige que a organização "selecione auditores e conduza auditorias que assegurem a
**objetividade e a imparcialidade** do processo" — e a regra basilar (ISO 19011) de que **o auditor não
audita o próprio trabalho**.

**Situação declarada e como é tratada:**

- A **implementação** do SGSI/SGPI da TWYN foi conduzida pela **Bekaa Tecnologia Ltda** (CNPJ
  28.811.817/0001-69), sob responsabilidade técnica de **Ricardo Esper** (consultor).
- A **ness** integra o mesmo grupo da Bekaa — **fato divulgado abertamente** neste instrumento.
- **Mitigação (segregação de equipe):** a auditoria interna é executada por **equipe segregada** da
  ness — **Monica Yoshida Barbosa** — que **não participou** da implementação do SGSI/SGPI da TWYN e
  **não tem sobreposição** com o Ricardo Esper nem com qualquer consultor do engajamento ENG-2026-001.
- Com isso, a ameaça de **auto-revisão** (auditar o próprio trabalho) **fica afastada**. O vínculo de
  grupo é **divulgado** e gerido pela declaração de imparcialidade (item 3), compatível com o requisito
  da auditoria **interna** (9.2) — que **não** é o veto de consultoria do organismo certificador
  (ISO 17021).

> ⚠️ **Risco residual sinalizado:** um auditor de Stage 2 pode questionar a relação de grupo. A defesa é
> a documentação deste pacote (segregação de equipe comprovada + declaração assinada + credenciais).
> Este instrumento **não** substitui o julgamento do organismo certificador.

### 2.1 OM-0 — ~~Participação da ness na implementação~~ **RETRATADO** (premissa incorreta)

> ⚠️ **OM-0 RETRATADO em 2026-08-26.** Foi **levantado e depois invalidado** — registro mantido por
> transparência do processo (não é achado ativo e **não** vai ao organismo certificador como tal).

**O que foi levantado:** a verificação do campo `uploaded_by` no nISO mostrou **9 evidências** centrais
do SGSI carregadas sob o identificador **`consultant@ness.io`**. A consultoria **inferiu** — pela
semelhança do nome — que `ness.io` seria o domínio da auditora **ness Processos e Tecnologia Ltda**, e
concluiu que a ness teria atuado como implementadora (autorrevisão).

**Por que foi retratado:** o **DPO/consultor (resper@bekaa.eu) confirmou que `ness.io` NÃO é domínio da
ness** — a inferência estava **errada**. Sem esse vínculo, **não há** evidência de que a auditora tenha
participado da implementação. A conclusão de "autorrevisão organizacional" **cai**; a posição de
independência volta a ser a da seção 2 (segregação de equipe + divulgação do vínculo de grupo).

**Lição registrada:** identidade de nome **não** é identidade de entidade — o identificador do uploader
deveria ter sido **verificado** antes de virar achado. `consultant@ness.io` é um **identificador não
atribuído/genérico** no store (a par de `u1`, `system`), provavelmente dado de seed do nISO.

**Ponto de higiene remanescente (não é independência):** convém o operador do nISO **esclarecer/normalizar**
quem é `consultant@ness.io` no `uploaded_by` (parte da higiene do store), para não gerar dúvida futura.

## 3. Declaração de Imparcialidade e Independência (a ser assinada pela ness)

> _A ness Processos e Tecnologia Ltda e a auditora Monica Yoshida Barbosa declaram, para os fins da
> auditoria interna 9.2 do SGSI/SGPI da TWYN:_

1. A auditora designada **não participou**, sob qualquer forma, da **implementação/adequação** do
   SGSI/SGPI da TWYN (engajamento ENG-2026-001).
2. A auditora **não tem vínculo funcional** com o Ricardo Esper nem com a equipe de consultoria da
   Bekaa que atuou na implementação.
3. A relação de **grupo entre ness e Bekaa é divulgada** e não interfere na objetividade do processo,
   assegurada pela segregação de equipe.
4. A ness **não é** o organismo certificador do Stage 1/2 e **não tem interesse** no resultado da
   certificação além da execução técnica desta auditoria.
5. A auditora atuará com **objetividade, imparcialidade e sigilo**, reportando exclusivamente à
   **direção da TWYN**.

**Assinatura ness / Monica Yoshida Barbosa:** ______________________  Data: ____/____/______

## 4. Competência (a comprovar — anexar)

- [ ] **Credencial de Auditor Líder ISO/IEC 27001** de Monica Yoshida Barbosa (ex.: IRCA / Exemplar
      Global) — anexar certificado.
- [ ] Desejável: competência em **ISO/IEC 27701 / LGPD** — anexar comprovação.
- [ ] **Currículo** resumido demonstrando experiência em auditoria de SGSI.

## 5. Escopo e critérios da auditoria interna

- **Normas de referência:** ISO/IEC 27001:2022 (SGSI) + ISO/IEC 27701:2025 (SGPI).
- **Critérios:** requisitos das cláusulas 4–10 da 27001; controles aplicáveis do Anexo A (SoA); controles
  aplicáveis do 27701 (Controlador); políticas e procedimentos internos da TWYN.
- **Fonte da verdade:** nISO (projeto `mr9c1qugo16zic2eko`) + repositório ISMS.
- **Cobertura mínima (checklist):**
  1. **Cláusulas 4–10** (contexto, liderança, planejamento, apoio, operação, avaliação de desempenho,
     melhoria) — evidência de operação, não só de documento.
  2. **SoA × realidade:** amostragem de controles `Implemented`/`In Progress` contra evidência objetiva
     no nISO.
  3. **Controles técnicos** (logs, monitoramento, criptografia, acesso) — verificar evidência de
     operação efetiva (inclui exports do AWS da TI).
  4. **SGPI 27701:** ROPA, DPIA, direitos dos titulares (DSAR), minimização, base legal (Art. 11 II 'g').
  5. **Governança de privacidade:** arranjo de DPO, canal `dpo@t4isb.com`, contrato e ato de nomeação.
  6. **Registro de não conformidades** e encaminhamento para tratamento (cl. 10.2).

## 6. Entregáveis da auditoria (pela ness)

- **Plano de auditoria** (datas, amostragem, equipe).
- **Relatório de auditoria interna** assinado, com achados, não conformidades e oportunidades de melhoria.
- **Registro de não conformidades** (para a TWYN tratar via 10.2).

## 7. Governança do programa (pela TWYN)

- A **direção da TWYN** recebe o relatório, delibera sobre não conformidades e registra ações
  corretivas — **antes** de acionar o organismo certificador.
- A consultoria (Bekaa/Aegis) **não** participa da execução nem do julgamento desta auditoria.

## 8. Pendências

- [ ] Assinatura da **Declaração de Imparcialidade** (item 3) pela ness/Monica.
- [ ] Anexo das **credenciais** (item 4).
- [ ] Aprovação/assinatura da **direção da TWYN**.
- [ ] Agendamento e execução da auditoria; emissão do relatório.
