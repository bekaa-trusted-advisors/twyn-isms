# Prompt — Defeitos técnicos da PLATAFORMA nISO (report ao time do produto)

> Para reportar ao time de desenvolvimento do nISO. Trata do **comportamento do software/API**, não
> dos dados do projeto TWYN. Observado via API v1 (`https://niso.ness.workers.dev`) com chave de papel
> `consultant`. Nenhum segredo é reproduzido aqui.

---

```
Reporte técnico — comportamentos da plataforma nISO (API v1) que aparentam ser defeitos:

## SEGURANÇA (prioritário)
1) Exposição de credencial: GET /api/v1/projects/{id} retorna o campo `repository_token` com o valor
   em TEXTO CLARO no corpo da resposta. A API não deveria retornar campos de credencial; o segredo
   deveria ser cifrado em repouso e redigido/omitido na resposta. Verificar em todos os projetos.

## ESCRITA DE CONTROLE (PUT /api/v1/controls/{id})
2) No-op silencioso: enviar `maturity` (isolado ou junto com `status`) retorna HTTP 200, mas o valor
   NÃO é persistido (GET seguinte mostra o valor antigo). Esperado: persistir, ou retornar erro
   explícito de "campo não editável". 200 em campo ignorado induz a erro.
3) Campos de aprovação imutáveis sem aviso: enviar `ciso_approved_by`/`ceo_approved_by` = null é
   ignorado (200, sem efeito). Não há caminho de API para RETIRAR uma aprovação. Se é intencional,
   documentar; se não, expor endpoint/permite limpar aprovação.

## PROJETO (PUT /api/v1/projects/{id})
4) Mensagem de erro enganosa: enviar `standards` retorna 400 {"error":"Nothing to update"} mesmo com
   o campo presente. Se o campo é derivado/read-only, retornar mensagem explícita ("field not editable")
   em vez de "Nothing to update".

## EVIDÊNCIAS
5) Sem endpoint de atualização/re-vínculo de evidência: PUT /api/v1/evidence/{id} → 404 e
   /api/v1/projects/{id}/evidence/{id} → 404. Não há como (re)associar uma evidência a um controle via
   API. Se o vínculo é só-UI, é uma lacuna de capacidade; se existe rota, ela não está acessível/documentada.
6) Normalização de enum: `evaluation_status` aceita valores com caixa inconsistente ("Conforme" e
   "conforme" coexistem). A plataforma deveria normalizar o enum.

## CONSISTÊNCIA / DESCOBERTA DE API
7) Verbos inconsistentes: PATCH /api/v1/controls/{id} → 404, enquanto PUT funciona. OPTIONS retorna
   204 com header `Allow` vazio (sem descoberta de métodos). Não há /openapi.json nem índice de rotas.
8) Rota documentada ausente: POST/GET /api/v1/projects/{id}/control-adequacao → 404 (a rota de
   "adequação de controle" citada não responde). Confirmar o path correto.
9) Política de papel: GET /api/v1/assessments?project_id={id} → 403 para a chave `consultant`.
   Confirmar se o papel consultor deveria ter leitura de assessments (senão, é policy esperada).

Para cada item: confirmar se é bug, comportamento intencional, ou rota/documentação divergente.
```

---

> **Nota:** achados de **dado do projeto TWYN** (token específico a rotacionar, riscos a reabrir,
> metadados a preencher, papéis DPO/CISO, evidências pending/órfãs) **não** entram aqui — são tratados
> nas issues internas do repositório (ex.: #23 segurança), não como bug da plataforma.
