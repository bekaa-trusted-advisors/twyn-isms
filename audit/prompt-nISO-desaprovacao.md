# Prompt para o nISO — liberar DESAPROVAÇÃO (revogação de sign-off) para o papel Consultor

> **Tipo:** requisito/defeito de plataforma (não é seed de projeto).
> **Origem:** ENG-2026-001 (consultoria de adequação ISO 27001/27701 — projeto `mr9c1qugo16zic2eko`).
> **Data:** 2026-08-21.
> **Cole o texto da seção "Prompt" abaixo no canal do nISO.**

---

## Prompt

Preciso de uma capacidade que hoje **não existe** na API do nISO: **desaprovar / revogar a assinatura (sign-off) de um controle**. Hoje só é possível *aprovar*, e não há caminho para *desfazer* uma aprovação — o que impede corrigir aprovações inválidas ou sem lastro. Isso precisa ser uma **tarefa que o papel Consultor (chave de escrita) possa executar**, sem exigir a senha do aprovador original nem acesso de admin.

### Contexto / por que é necessário

No projeto `mr9c1qugo16zic2eko`, 60 controles ISO 27001:2022 estão com `ciso_approved_by = "Ricardo Esper"`, sendo que:
- Ricardo Esper é **consultor externo**, **não é CISO** da organização (cargo de CISO **vago**);
- o registro foi gerado por **agente automático** (`ciso_approved_ip = 127.0.0.1`, `ciso_approved_ua = "System Agent Automator"`), **sem lastro de assinatura humana**.

Por integridade de auditoria, essas aprovações precisam ser **revogadas** (uma aprovação sem lastro não pode permanecer como válida). Como consultor de adequação, preciso conseguir fazer isso.

### Limitação observada hoje (evidências)

- `PUT /api/v1/controls/{id}` com campos de aprovação (`ciso_approved_by`, `ciso_approved_at`, `ciso_approved_ip`, `ciso_approved_ua`) → os campos são **silenciosamente ignorados**: enviados sozinhos retornam `400 {"error":"Nothing to update"}`; enviados junto de `status` retornam `{"ok":true}` **mas o valor de aprovação não muda**. Apenas `status` e `description` são graváveis.
- Não existe endpoint de reversão: `POST /controls/{id}/unapprove`, `/reject`, `/revoke`, `/reset-approval`, `/disapprove` → todos **404**.
- `POST /controls/{id}/approve` existe, porém exige `password` e **só aprova** (fluxo unidirecional). Não há equivalente para desaprovar.

### Requisito

Expor uma operação de **revogação de aprovação** que:
1. Seja executável pelo **papel Consultor / chave de escrita** (`X-API-Key`, mcp-key-1), **sem** a senha do aprovador e **sem** acesso admin.
2. **Limpe** os campos de aprovação do controle para o papel indicado (`ciso_*` e/ou `ceo_*`): `*_approved_by`, `*_approved_at`, `*_approved_ip`, `*_approved_ua`.
3. **Registre trilha de auditoria da revogação**: quem revogou (identidade da chave/consultor), timestamp, e um **motivo** obrigatório — sem apagar o histórico de quem havia aprovado antes.
4. Suporte operação **individual e em lote** (revogar N controles de um projeto de uma vez).

### Forma de API sugerida (a critério de vocês)

```
POST /api/v1/controls/{id}/revoke-approval
Body: { "role": "ciso" | "ceo", "reason": "aprovação sem lastro — assinante não é CISO; cargo vago" }
→ limpa os campos <role>_approved_* e grava revoked_by / revoked_at / revoke_reason
```
Variante em lote:
```
POST /api/v1/projects/{project_id}/revoke-approvals
Body: { "role": "ciso", "control_ids": ["ctrl-a51", ...], "reason": "..." }
```

### Critério de aceite

- Com a chave de escrita do consultor, uma chamada de revogação zera `ciso_approved_by` (e correlatos) do controle-alvo e isso **persiste** numa leitura subsequente (`GET /controls?project_id=...`).
- A revogação fica registrada (revogante + timestamp + motivo).
- Não é exigida a senha do aprovador nem privilégio de admin.

### Enquanto não existir

Registramos a desaprovação como **caveat no campo `description`** dos 60 controles afetados (único campo gravável), declarando a aprovação de CISO **inválida/desaprovada** e pendente de assinatura de CISO designado. Esse texto deverá ser **removido** quando a revogação nativa estiver disponível e os metadados `ciso_approved_*` forem efetivamente limpos.
