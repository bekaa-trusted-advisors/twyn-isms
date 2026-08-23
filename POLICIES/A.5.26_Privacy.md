# SGP-IRP-001: Plano de Resposta a Incidentes de Privacidade (Brechas PII) — TWYN
**ISO/IEC 27701:2025 Anexo A: A.3.12 (Resposta a incidentes) & LGPD Artigo 48**

---

**Controle de Documento**

| Campo | Valor |
|-------|-------|
| **Document ID** | SGP-IRP-001 |
| **Version** | 1.0 (Oficial) |
| **Elaborado por** | Ricardo Esper (Consultor) |
| **Aprovado por** | Nizar Elouaer (CTO / Liderança de SI) |
| **Data de Emissão** | 20/07/2026 |
| **Status** | Aprovado |

---

## 1. Diretrizes de Resposta a Incidentes de Privacidade

Este plano define a rotina de atuação do CSIRT (Time de Resposta a Incidentes) em caso de suspeita ou confirmação de vazamento de dados pessoais (inclusive templates biométricos).

---

## 2. Fluxo de Atuação e Contenção

1.  **Detecção & Triagem:** Recebimento e triagem do alerta do AWS GuardDuty ou do Datadog pela CIO Humberto Oliveira. Havendo indício de exposição de PII, o Encarregado (DPO), Bekaa Tecnologia Ltda (PJ), declara o início do incidente de privacidade.
2.  **Contenção Lógica Imediata:** sob a coordenação da CIO, o DevOps (Marcelo Mascarenhas) isola os bancos de dados RDS Aurora, revoga chaves IAM suspeitas e bloqueia portas VPC.
3.  **Avaliação de Impacto (Risco):** O Encarregado (DPO), Bekaa Tecnologia Ltda (PJ), avalia a severidade. Como os hashes biométricos armazenados são irreversíveis e pseudoanônimos (desprovidos de CPFs ou nomes civis diretos), a probabilidade de reidentificação dos titulares por terceiros é classificada como **Baixa/Nula**.

---

## 3. Fluxo de Comunicação e Prazos

### ANPD (Autoridade Nacional):
*   Se a triagem identificar que o vazamento expõe dados biométricos sensíveis e de alguma forma há risco para os titulares, o DPO enviará a notificação à ANPD em até **2 dias úteis** da ciência do fato (conforme regulamento oficial da ANPD).

### Clientes B2B (Co-controladores):
*   O CTO Nizar Elouaer notificará formalmente os administradores dos clientes B2B afetados em até **24 horas** após a confirmação técnica do incidente, permitindo que eles alinhem suas esferas de atendimento.

---

## 4. Revisão e Simulações

Este plano é testado semestralmente pelo comitê de segurança através de simulações de vazamento de tabelas.

**Nizar Elouaer**  
CTO / Liderança de SI  
TWYN T4ISB DO BRASIL TECNOLOGIA E PARTICIPACOES LTDA (CNPJ: 31.122.819/0001-55)
*Assinado eletronicamente via TWYN GRC Portal em 21/07/2026 18:00 BRT (IP: 191.189.44.112, Hash: 9b8a035b61613d0db34782e7df22e033)*
