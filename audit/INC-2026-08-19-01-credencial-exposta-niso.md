# Registro de Incidente de Segurança — INC-2026-08-19-01

| Campo | Valor |
|---|---|
| **ID** | INC-2026-08-19-01 |
| **Engajamento** | ENG-2026-001 |
| **Data de detecção** | 2026-08-19 |
| **Detectado por** | Consultoria Aegis (sondagem da API do nISO) |
| **Classificação** | **Crítico** — exposição de credencial |
| **Ativo** | Integração nISO ↔ repositório GitHub (`bekaa-trusted-advisors/twyn-isms`) |
| **Controles relacionados** | A.5.24–A.5.26 (incidentes), A.8.24 (criptografia/segredos), 27701 A.3.26 |
| **Issue** | #23 |

## 1. Descrição

O registro do projeto no nISO (`GET /api/v1/projects/mr9c1qugo16zic2eko`) retorna o campo
**`repository_token` com uma credencial em TEXTO CLARO** no corpo da resposta da API. Qualquer portador
de uma chave de **leitura** da API obtém o segredo. O valor **não é reproduzido** neste registro (redigido).

## 2. Impacto

- Credencial de acesso ao repositório do ISMS exposta e potencialmente comprometida (foi lida via API).
- Fere gestão de segredos / não-armazenamento em texto claro (A.8.24 / POL-CRY-001).
- Defeito de plataforma (a API não deveria retornar campos de credencial) — reportado ao fornecedor
  do nISO (ver `audit/prompt-nISO-achados.md`).

## 3. Contenção / Erradicação (runbook)

1. **[URGENTE] Rotacionar a credencial na origem (GitHub):** revogar/regenerar o token/senha do
   repositório imediatamente. A credencial atual deve ser considerada **comprometida**.
2. **Atualizar o nISO** para usar a nova credencial **armazenada de forma segura** (cofre/secret,
   cifrada em repouso) — não em campo de texto claro exposto pela API.
3. **Remover a exposição:** garantir que a API do nISO deixe de retornar o campo de credencial
   (correção do fornecedor). Enquanto não corrigido, tratar toda chave de leitura como sensível.
4. **Verificar reuso:** confirmar se a mesma credencial foi usada em outros sistemas; se sim, rotacionar lá também.

## 4. Lições aprendidas / ações preventivas

- Segredos nunca em texto claro em plataforma GRC; usar secret manager / campos cifrados e redigidos na API.
- Revisar se outros projetos/campos do nISO expõem segredos (correção sistêmica de plataforma).
- Incluir "varredura de segredos expostos" na rotina de verificação do ISMS.

## 5. Status

- [ ] Credencial rotacionada na origem (GitHub) — **responsável: DevOps/CTO**
- [ ] nISO atualizado com credencial segura — **DevOps + admin nISO**
- [ ] Exposição na API corrigida pelo fornecedor — **nISO (bug report enviado)**
- [ ] Verificação de reuso concluída — **DevOps**

> Registro de incidente conforme gestão de incidentes do SGSI. Encerrar (#23) quando todos os itens acima estiverem concluídos.
