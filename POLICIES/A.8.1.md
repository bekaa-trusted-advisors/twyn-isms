# POL-EPP-001 — Segurança de Dispositivos de Usuário Final (Endpoints)
**ISO/IEC 27001:2022 A.8.1**

---

**Controle de Documento**

| Campo | Valor |
|---|---|
| **Document ID** | POL-EPP-001 |
| **Versão** | 1.0 (Rascunho) |
| **Elaborado por** | Consultoria Aegis (ENG-2026-001) |
| **A ser aprovado por** | Humberto Oliveira (CIO) · Kacio Lopes (CEO) |
| **Status** | `Rascunho — pendente de aprovação` |

---

## 1. Objetivo
Definir os controles mínimos de segurança para os endpoints (notebooks) usados pela equipe remota do
TWYN, que acessam recursos AWS, GitHub e dados corporativos.

## 2. Baseline obrigatório
1. **Criptografia de disco** integral (FileVault/BitLocker/LUKS).
2. **Antimalware** ativo e atualizado (`A.8.7` — POL-MAL-001).
3. **Atualizações** automáticas de SO e aplicações críticas.
4. **Bloqueio automático** de tela e senha forte/biometria de desbloqueio (`A.7.7`).
5. **Menor privilégio** local; sem conta de administrador para uso diário.
6. **Acesso corporativo** só a partir de dispositivo em conformidade (ver `A.6.7` — trabalho remoto).

## 3. Gestão
Inventário de dispositivos e verificação periódica de conformidade; em desligamento, revogação de
acessos e, quando aplicável, sanitização de mídia (`POL-GOV-001` §4; `POL-HR-001`).

## Aprovação

Documento em rascunho — pendente de aprovação. Nenhuma assinatura foi aposta por terceiros.

Aprovação: ______________________________  Data: ____ / ____ / ______
