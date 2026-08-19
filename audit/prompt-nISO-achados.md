# Prompt — Achados de plataforma/dados do nISO (TWYN, ENG-2026-001)

> Cole o bloco abaixo no assistente/admin do nISO. Lista os achados encontrados via API e a ação
> requerida de cada um. Não contém segredos. Projeto: `mr9c1qugo16zic2eko`.

---

```
Contexto: projeto TWYN Face ID Platform (mr9c1qugo16zic2eko), SGSI 27001:2022 + SGPI 27701:2025,
papel Controlador. Foram identificados os achados abaixo no estado de dados/configuração do nISO.
Trate cada um; onde for correção de dado, proponha a mudança para aprovação humana antes de aplicar.

## CRÍTICO
1) Segredo em texto claro: o registro do projeto expõe o campo `repository_token` com uma credencial
   em texto claro, retornada pela API de leitura. Ação: (a) remover/cifrar o campo (não armazenar
   segredo em texto claro), (b) sinalizar rotação da credencial na origem, (c) verificar se outros
   projetos/campos expõem segredos de forma semelhante (correção de plataforma).

## GOVERNANÇA / PAPÉIS (decisão do cliente)
2) DPO: designar Humberto Oliveira como Encarregado (DPO) até o fim do processo de certificação.
   Atualizar a designação onde o DPO estiver nomeado.
3) Ricardo Esper é APENAS consultor (Aegis). Remover toda atribuição dele como CISO e como DPO.
   Em particular: o campo `ciso_approved_by` = "Ricardo Esper" consta em ~60 controles — essa
   atribuição é inválida e deve ser removida/reatribuída ao CISO real (a definir).
4) Identidades duplicadas do mesmo indivíduo (ex.: "resper@bekaa.eu", "Ricardo Esper",
   "Ricardo Esper (DPO)") devem ser unificadas para rastreabilidade.

## INTEGRIDADE DE DADOS
5) Aprovação sem lastro: ~17 controles constam assinados (ciso/ceo_approved_by) sem evidência
   anexada. Retirar a aprovação até haver evidência, ou anexar evidência objetiva.
6) Riscos desincronizados: os 12 riscos estão todos como "Mitigated". Ao menos 3 (risk-twyn-03/04/05)
   apoiam-se em controles com status Missing (A.8.12/A.5.17/A.8.9) e devem ser reabertos ("Open")
   até implementação/evidência. Revisar também a plausibilidade de "todos Mitigated".
7) Metadados do projeto incompletos: client_name (vazio), sector, cnpj, employee_count (nulos).
   Preencher (contexto da organização — cláusula 4).
8) Evidências: 42 itens "pending" (avaliar), 7 órfãs (control_id inexistente — religar/remover),
   e casing inconsistente do status ("Conforme" vs "conforme" — padronizar).

## LIMITES DE PLATAFORMA OBSERVADOS (para o time do nISO)
9) Via API (papel consultant), o PUT de controle só grava `status` e `description`; `maturity` e os
   campos de aprovação são imutáveis, e não há rota de re-vínculo de evidência (`PUT /evidence` → 404).
   Confirmar se essas operações (zerar maturidade, retirar aprovação, religar evidência) existem no
   UI/admin — hoje são bloqueadas por API.

## PEDIDO
Para cada achado, retorne: (a) se é corrigível no nISO e como; (b) a proposta de correção; (c) o que
depende de decisão humana. Não declare nenhum controle conforme sem evidência objetiva verificável.
```

---

## Referência (uso interno — não colar)
- Achado 1 registrado em **issue #23** (segurança).
- Achados 5/6 relacionam-se às issues **#8** (assinatura sem lastro) e à reconciliação de riscos.
- Decisão de papéis (2/3/4): DPO = Humberto; Ricardo = consultor. Ajuste dos documentos de nomeação do
  DPO e remoção das referências de CISO/DPO do Ricardo tratados como workstream à parte (não-cross agora).
