# Relatório de Reconciliação de Prontidão — ENG-2026-001

| Campo | Valor |
|---|---|
| **Engajamento** | ENG-2026-001 |
| **Cliente** | TWYN — Face ID Platform |
| **Escopo normativo (contratado)** | ISO/IEC 27001:2022 (SGSI) + ISO/IEC 27701:2025 (SGPI) |
| **Modo** | CONSULTOR — reconciliação de prontidão |
| **Base** | Leitura dos artefatos versionados na `main` (README, SOA, RISKS, ROPA, POLICIES/, EVIDENCE/) |
| **Data** | 2026-08-18 |
| **nISO** | Não sincronizado nesta análise (handshake pendente) |

> **Natureza deste documento.** Esta é uma **reconciliação de consultor** — leitura
> crítica dos artefatos para identificar inconsistências e lacunas antes de encarar
> um organismo certificador. **Não é** a auditoria interna da cláusula 9.2 (que exige
> agente/sessão independente) **nem** um parecer de certificação. Nenhuma evidência
> foi criada ou completada; lacunas são declaradas como gap.

---

## Sumário executivo

O repositório se declara **`Audit Ready` / IPC 100%** (`README.md` l.12-13; `SOA.md` l.4).
A reconciliação **não sustenta** essa afirmação: há contradições materiais entre os
próprios artefatos e sinais de integridade que **não resistiriam a um Stage 1/Stage 2**.
Os pontos de **severidade alta** abaixo devem ser resolvidos antes de qualquer submissão
a certificador. Há também uma **divergência de versão** (artefatos em 27701:2019 vs. escopo
contratado 27701:2025) que exige remapeamento.

Ponto positivo objetivo: os **checksums SHA-256** publicados em `EVIDENCE/README.md`
**conferem** com os arquivos físicos (amostra verificada) — a integridade referencial do
índice está correta.

---

## Achados — Severidade ALTA

**F1 — "IPC 100% / Audit Ready" contradiz o próprio SoA.**
`SOA.md` cataloga 93 controles com a seguinte distribuição real de status:
`Implemented` = 49 · `Missing` = 27 · `Not Applicable` = 14 · `Approved` = 3.
27 controles aplicáveis marcados `Missing` são incompatíveis com "100%".
→ *Recomendação:* recalcular o IPC a partir do estado real e corrigir README/SOA.

**F2 — Contradições de campo no SoA (status × maturidade × evidência).**
Vários controles estão `Missing` porém com maturidade 3–4 e evidência/aprovação:
A.6.3, A.5.17, A.5.21, A.5.22, A.5.26, A.5.30, A.8.9, A.8.12, A.8.13.
Caso emblemático: **A.8.13 (Backup)** marcado `Missing` enquanto o texto diz
"AWS Backup configurado… RTO 4h/RPO 1h validados… (Aprovado por CISO/CEO)" (`SOA.md` l.85).
Isso indica **dessincronização de dados** (provável divergência repo ↔ nISO) e mina a
confiabilidade do SoA como um todo.
→ *Recomendação:* reconciliar campo a campo contra a fonte da verdade (nISO) e
reprocessar status/maturidade de forma consistente.

**F3 — Controles `Implemented` com maturidade 0.**
A.6.1, A.6.2, A.6.4, A.6.8, A.5.31 constam `Implemented` com CMM 0 e justificativas
genéricas em inglês ("Background verification for all personnel", etc.), sem lastro.
→ *Recomendação:* rebaixar a `Planned/Partial` ou anexar evidência que justifique
maturidade > 0.

**F4 — RISKS × SoA: riscos "Mitigados" por controles inexistentes.**
`RISKS.md` declara riscos `Mitigated` "via conformidade técnica" de controles que o SoA
marca `Missing`:
- `risk-twyn-04` → A.5.17 (SoA: **Missing**)
- `risk-twyn-03` → A.8.12 DLP (SoA: **Missing**)
- `risk-twyn-05` → A.8.9 (SoA: **Missing**)

Tratamento de risco não pode se apoiar em controle não implementado.
→ *Recomendação:* reabrir esses riscos (status ≠ Mitigated) ou implementar/evidenciar os
controles citados; distinguir risco inerente × residual.

**F5 — Integridade/autenticidade das evidências.**
Todas as ~47 evidências em `EVIDENCE/README.md` têm **data de coleta única: 2026-07-27**,
e os artefatos de auditoria são **stubs**: `Parecer_Auditoria_Estagio1_Fase39.txt` = 17 linhas;
`Relatorio_Auditoria_Estagio2_Fase40.txt` = 19 linhas; `Carta_de_Mandato_Fase0.txt` = 26 linhas.
Uma jornada de 41 fases (Fase 0 → 40), com pareceres de Estágio 1 **e** Estágio 2 já
"emitidos", toda gerada no mesmo dia, **não resiste ao escrutínio de um certificador** e é
incompatível com a premissa do engajamento (alcançar Stage 1/Stage 2).
→ *Recomendação:* tratar essas evidências como **rascunhos/placeholders**, não como
evidência objetiva; reconstituir a trilha real com datas e autoria verificáveis ao longo do
tempo. (Os pareceres de Estágio 1/2 pré-existentes **não** substituem a auditoria de
certificação real.)

---

## Achados — Severidade MÉDIA

**F6 — Cobertura 27701 ausente no SoA.**
O SoA afirma catalogar "controles de privacidade da 27701" (l.6), mas a tabela contém apenas
o Anexo A do 27001 (A.5–A.8). Não há o conjunto de controles específicos do 27701 (por papel
de **controlador/operador** de PII). Existem políticas de privacidade (`SGP-*`) em `POLICIES/`,
porém sem SoA de privacidade correspondente.
→ *Recomendação:* montar a extensão de SoA do SGPI com os controles do 27701 aplicáveis ao
papel de **Controlador Independente** declarado no ROPA.

**F7 — Divergência de versão 27701:2019 → 2025.**
`SOA.md` (l.3/6), `ROPA.md` (l.3) e `POLICIES/README.md` (l.3) referenciam **27701:2019**;
o escopo contratado é **27701:2025**. A revisão 2025 reestrutura o PIMS como sistema de gestão
autônomo (não mais mera extensão do 27001).
→ *Recomendação:* remapear cláusulas/controles para a estrutura 2025.

**F8 — Cobertura e mapeamento de políticas.**
37 arquivos de política para 93 controles; múltiplos controles `Implemented` sem política
correspondente no índice. Mapeamentos incoerentes: A.8.24 (Uso de Criptografia) → "SOP-HDN-001
Manual de Hardening" (`POLICIES/README.md` l.40); A.8.15 (Logs) → "Manual de Arquitetura Segura" (l.37).
→ *Recomendação:* revisar o mapa controle→documento e cobrir os controles aplicáveis sem política.

**F9 — Status divergente entre documentos.**
A.8.19 consta `APROVADA` no índice de políticas (`POLICIES/README.md` l.38) e `Missing` no
SoA (`SOA.md` l.91).
→ *Recomendação:* fonte única de verdade para status (nISO) e regeneração determinística dos docs.

**F10 — Governança, papéis e independência.**
O papel "CISO" no SoA é atribuído a pessoas diferentes (Ricardo Esper; Nizar Elouaer nos NA
físicos; **Humberto Oliveira** nos 3 controles `Approved`), e um mesmo indivíduo acumula
**DPO + CISO + Consultor** (Ricardo Esper — ver README e assinaturas do SoA). O acúmulo
compromete a segregação de funções (A.5.3) e a independência do DPO (relevante ao 27701) e da
auditoria interna (9.2).
→ *Recomendação:* formalizar o organograma do SGSI/SGPI com segregação e independência do DPO.

---

## Achados — Severidade BAIXA

- **F11 — Vocabulário de status inconsistente:** {`Implemented`, `Missing`, `Not Applicable`, `Approved`}. Padronizar (ex.: Implemented / Partially Implemented / Planned / Not Applicable).
- **F12 — Justificativas de "Não Aplicável" autocontraditórias:** A.7.10, A.7.13, A.7.14 marcados `Not Applicable` com texto "aplica-se a todas as organizações". Rever aplicabilidade.
- **F13 — Contagens divergentes:** `EVIDENCE/README.md` diz "41 fases" mas lista ~47 arquivos. Alinhar.
- **F14 — Caminhos locais Windows** (`file:///c:/Users/...`) embutidos em README/SOA/POLICIES/EVIDENCE — quebram fora da máquina de origem. Usar caminhos relativos.
- **F15 — Registro de riscos uniforme demais:** todos os 12 riscos `Low`/`Mitigated`, sem scores numéricos apesar da metodologia 1–5, sem inerente × residual — implausível para plataforma de biometria sensível.

---

## Estado real do SoA (reconciliado)

| Status | Qtde | Observação |
|---|---:|---|
| Implemented | 49 | inclui casos com maturidade 0 (F3) |
| Missing | 27 | vários com maturidade/evidência inconsistentes (F2) |
| Not Applicable | 14 | rever F12 |
| Approved (não-padrão) | 3 | A.8.24 / A.8.25 / A.8.28 (F11) |
| **Total** | **93** | contagem correta |

---

## Próximos passos propostos (para aprovação)

1. **Reconciliar status/maturidade do SoA** contra o nISO (fonte da verdade) — resolve F2, F3, F9.
2. **Corrigir o IPC e a narrativa "Audit Ready"** para refletir o estado real — F1.
3. **Reabrir riscos apoiados em controles `Missing`** e separar inerente × residual — F4, F15.
4. **Construir a extensão de SoA do SGPI (27701:2025)** e remapear a versão — F6, F7.
5. **Reconstituir a trilha de evidências** com datas/autoria reais; tratar os stubs como rascunho — F5.
6. **Formalizar governança/segregação** (organograma, independência do DPO) — F10.
7. **Higiene documental** (vocabulário, caminhos relativos, contagens) — F11–F14.

> **Independência (lei Aegis):** todos os itens acima são de **consultoria/adequação**. A
> verificação de conformidade final (auditoria interna 9.2) desses mesmos artefatos deve ser
> conduzida por **sessão/agente independente** — não por quem os implementa.

> **nISO:** qualquer gravação no estado GRC do cliente segue o ciclo **propõe → humano aprova
> → aplica** e depende do handshake nISO (chave real como servidor MCP; hoje pendente).
