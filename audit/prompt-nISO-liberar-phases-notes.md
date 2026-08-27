# Pedido ao desenvolvedor do nISO — liberar escrita de `phases.notes` (+ corrigir `scope`)

> Para enviar ao **time de desenvolvimento do nISO**. Trata do **comportamento da API**, não de dados
> sensíveis. Observado via API v1 (`https://niso.ness.workers.dev`) com chave de papel `consultant`,
> projeto `mr9c1qugo16zic2eko`. **Nenhum segredo é reproduzido aqui** (a `X-API-Key` nunca aparece).

---

## Resumo do pedido (2 itens)

1. **Liberar a gravação do campo `notes` das fases** (`phases.notes`) pela API do papel `consultant` —
   exatamente como vocês liberaram o campo `owner` dos controles em 2026-08-26.
2. **Corrigir o campo `scope` do projeto**: hoje diz `us-east-1`; a residência real do dado é
   **`sa-east-1`** (São Paulo/Brasil). Ou liberar a escrita de `scope` via API, ou corrigir no banco.

---

## Item 1 — `phases.notes` não persiste (parece no-op silencioso)

**Contexto:** a consultoria precisa **repopular as notas das 41 fases** da trilha de implementação
(campo `notes`, hoje vazio em todas). O conteúdo já está pronto (ver
`audit/ENG-2026-001-trilha-prontidao-respostas.md`, anexo "Notas por fase").

**Comportamento observado (API v1):**

```
# Endpoint de leitura (funciona):
GET /api/v1/projects/{projectId}/phases            -> 200, retorna as 41 fases com {id, phase_number,
                                                       title, status, notes, completed_at, created_at}

# Escrita de STATUS (funciona):
PUT /api/v1/projects/{projectId}/phases/{phaseId}   body {"status":"completed"}  -> {"ok":true}  (persiste)

# Escrita de NOTES (NÃO persiste — parece no-op silencioso):
PUT /api/v1/projects/{projectId}/phases/{phaseId}   body {"notes":"texto..."}    -> {"ok":true}
   ...mas o GET seguinte mostra notes = null (o valor NÃO foi gravado)

# Enviar notes junto com status também não grava o notes:
PUT ... body {"status":"completed","notes":"texto..."}  -> {"ok":true}  (status ok; notes ignorado)

# Nomes alternativos de campo não são reconhecidos:
PUT ... body {"note":"..."}     -> 400 {"error":"Nothing to update"}
PUT ... body {"content":"..."}  -> 400 {"error":"Nothing to update"}
PUT ... body {"zzz":"..."}      -> 400 {"error":"Nothing to update"}   (campo desconhecido)

# Outros verbos/rotas não existem:
PATCH /api/v1/projects/{projectId}/phases/{phaseId}        -> 404
POST  /api/v1/projects/{projectId}/phases/{phaseId}/notes  -> 404
```

**Diagnóstico:** o handler **reconhece** a chave `notes` (não retorna "Nothing to update", diferente de
`note`/`content`/`zzz`), mas **não a grava** — retorna `{"ok":true}` sem persistir. É o mesmo padrão que
o campo `owner` apresentava antes da liberação de 26/08.

**Pedido:** habilitar a persistência de `phases.notes` para o papel `consultant` via
`PUT /api/v1/projects/{projectId}/phases/{phaseId}` com body `{"notes":"..."}`, retornando
`{"ok":true}` **e** gravando. (Se por design `notes` deve ser read-only para `consultant`, por favor nos
digam — aí a consultoria entrega o payload e vocês aplicam pelo lado de vocês; ver payload abaixo.)

**Sugestão de UX de API (opcional):** quando um campo enviado for ignorado por não ser gravável, retornar
erro explícito (`field not writable`) em vez de `{"ok":true}` — o 200 em campo ignorado induz a erro (já
reportado para `maturity` e campos de aprovação em `prompt-nISO-achados.md`).

## Item 2 — `scope` do projeto com região errada (`us-east-1` → `sa-east-1`)

```
GET /api/v1/projects/mr9c1qugo16zic2eko
   -> scope: "Face ID Platform API + AWS Infrastructure (us-east-1) - Processamento de Biometria Facial..."
```

A residência real do dado é **`sa-east-1`** (Brasil) — a menção a `us-east-1` é resíduo (NC-04, já
corrigido em todo o repositório). Como `PUT /api/v1/projects/{id}` com `scope` não surtiu efeito pela
chave `consultant`, pedimos **corrigir `us-east-1` → `sa-east-1`** no campo `scope` (ou liberar sua
escrita via API). Texto-alvo:

```
Face ID Platform API + AWS Infrastructure (sa-east-1) - Processamento de Biometria Facial
(Vetorização Matemática Irreversível sob LGPD Art. 11, II, 'g')
```

---

## Payload pronto (mapa `phase_number → phase_id`)

Se preferirem aplicar as notas do lado de vocês (em vez de liberar a escrita), este é o mapa de IDs das
fases do projeto `mr9c1qugo16zic2eko`. O **texto de cada nota** está no anexo "Notas por fase" de
`audit/ENG-2026-001-trilha-prontidao-respostas.md` (uma linha por fase, 0–40).

| # | phase_id | status | título |
|---|---|---|---|
| 0 | `mr9c1qygum0q35hgsa` | completed | Mobilização e Mandato |
| 1 | `mr9c1qygbso4iblp1zf` | completed | Entrevista Executiva |
| 2 | `mr9c1qygni5z1a94q8` | completed | Entrevistas por Trilha |
| 3 | `mr9c1qyghbcw2qh6a96` | completed | Definição de Escopo |
| 4 | `mr9c1qygzvwi1ltq3` | completed | Gap Assessment |
| 5 | `mr9c1qyg0z95ycluwvwe` | completed | Governança e Papéis |
| 6 | `mr9c1qygsijj5dog3sq` | completed | Contexto e Partes Interessadas |
| 7 | `mr9c1qygxscjfvy8qdf` | completed | Inventário de Ativos e Dados |
| 8 | `mr9c1qyg0z9h1j7vbb6` | completed | Mapeamento de Processos |
| 9 | `mr9c1qygotweql79naq` | completed | Riscos de Segurança |
| 10 | `mr9c1qyg6imi62bc6zv` | completed | Riscos de Privacidade |
| 11 | `mr9c1qygzjuui504wlh` | completed | Tratamento de Riscos |
| 12 | `mr9c1qygqbvtqk5dy9` | completed | SoA do SGSI |
| 13 | `mr9c1qyg8xej49raqqf` | completed | SoA do SGPI |
| 14 | `mr9c1qygl1rq5d932w` | completed | Arquitetura Documental |
| 15 | `mr9c1qygwiv32il12ss` | completed | Controles Organizacionais |
| 16 | `mr9c1qygo24pjfqqf5` | completed | Controles de Pessoas |
| 17 | `mr9c1qyg5thlyr5z6sk` | completed | Controles Físicos |
| 18 | `mr9c1qyg1lp1zs9t0u6` | completed | Controles Tecnológicos |
| 19 | `mr9c1qyg6vamukhg117` | completed | Desenvolvimento Seguro |
| 20 | `mr9c1qyghl22cwk6tej` | completed | Cloud, DevOps e SRE |
| 21 | `mr9c1qyg4snag96tw3r` | completed | Programa de Privacidade |
| 22 | `mr9c1qygn4ll59u79ek` | completed | Privacy by Design |
| 23 | `mr9c1qygp7etb0se65l` | completed | Direitos dos Titulares |
| 24 | `mr9c1qyggvro1j0xl46` | completed | Consentimento e Bases Legais |
| 25 | `mr9c1qyg6mbz8wct8qm` | completed | Retenção e Descarte |
| 26 | `mr9c1qygz2ozyd42z8i` | completed | Transferências e Compartilhamento |
| 27 | `mr9c1qygdyfjr4tzhi8` | completed | Fornecedores e Operadores |
| 28 | `mr9c1qygh9uyoyuoj1u` | completed | Incidentes |
| 29 | `mr9c1qygfhh424zk1qq` | completed | Treinamento |
| 30 | `mr9c1qyggwlt1m3iyzh` | completed | Monitoramento e Métricas |
| 31 | `mr9c1qyg2ilcy79abxy` | completed | Auditoria Interna |
| 32 | `mr9c1qygqqgtgaqvjuf` | completed | Análise Crítica |
| 33 | `mr9c1qyg0skxolx5w6qi` | completed | Melhoria Contínua |
| 34 | `mr9c1qygbzhaf8qjt9` | pending | Certificação Estágio 1 |
| 35 | `mr9c1qygtz18lsslwso` | pending | Certificação Estágio 2 |
| 36 | `mr9c1qygkysz26g97h8` | pending | Pós-Certificação |
| 37 | `mr9c1qyghzch6w677wq` | pending | Gestão de Vulnerabilidades |
| 38 | `mr9c1qyg7q4n62sr406` | pending | Continuidade de Negócios |
| 39 | `mr9c1qyg2qgnzwcwd11` | pending | Segurança Física |
| 40 | `mr9c1qygwcslmznkb0c` | pending | Encerramento do Ciclo |

---

## Preferência da consultoria

**Opção A (preferida):** liberar `phases.notes` para o `consultant` → a consultoria aplica o lote por API
(propõe → aprovação humana → aplica), com verificação por GET, e mantém o log no `engagement.md`.

**Opção B:** vocês aplicam as 41 notas do lado do produto, a partir do anexo + mapa acima.

Em ambas, pedimos **confirmação por escrito** de qual campo passou a ser gravável (para atualizarmos a
tabela de capacidades da API em `audit/engagement.md`).
