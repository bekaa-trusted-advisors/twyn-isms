# POL-RMT-001 — Trabalho Remoto
**ISO/IEC 27001:2022 A.6.7**

---

**Controle de Documento**

| Campo | Valor |
|---|---|
| **Document ID** | POL-RMT-001 |
| **Versão** | 1.0 (Rascunho) |
| **Elaborado por** | Consultoria Aegis (ENG-2026-001) |
| **A ser aprovado por** | Humberto Oliveira (CIO) · Rosa Correia (COO) · Kacio Giuliano Lopes (CEO) |
| **Status** | `Rascunho — pendente de aprovação` |

---

> **Correção de escopo (ENG-2026-001):** o registro anterior indicava "nenhuma modalidade de trabalho
> remoto identificada", o que é **incorreto** — a equipe do TWYN é **100% remota**. Controle
> **aplicável**.

## 1. Objetivo
Definir os requisitos de segurança para o trabalho remoto, dado que toda a operação é distribuída.

## 2. Diretrizes
1. **Dispositivos:** endpoints com disco criptografado, antimalware e atualização automática
   (`A.8.1` — POL-EPP-001; `A.8.7`).
2. **Acesso:** MFA obrigatório e acesso aos recursos AWS/GitHub sob menor privilégio (`A.5.15`–`A.5.18`);
   preferência por acesso federado/zero-trust em vez de credenciais estáticas.
3. **Rede:** conexões cifradas (TLS/VPN quando aplicável); vedado uso de redes públicas sem proteção
   para acesso a dados **Restritos/Confidenciais** (`POL-GOV-001`).
4. **Ambiente:** tela limpa/bloqueio automático (`A.7.7`); vedado tratar biometria bruta fora dos
   sistemas autorizados.
5. **BYOD:** dispositivos pessoais só acessam recursos corporativos sob os controles mínimos acima.

## Aprovação

Documento em rascunho — pendente de aprovação. Nenhuma assinatura foi aposta por terceiros.

Aprovação: ______________________________  Data: ____ / ____ / ______
