# Revisão das Políticas — proporcionalidade e adequação ao projeto

| Campo | Valor |
|---|---|
| Engajamento | ENG-2026-001 |
| Data | 2026-08-19 |
| Base | Leitura de amostra (A.5.1, A.5.15, A.8.24, A.5.34) + dimensionamento das 37 |

## Veredito: **em grande parte, SIM** — bem escritas, proporcionais e adequadas

- **Substância real (não boilerplate):** as políticas são concretas e adaptadas ao contexto —
  templates biométricos, RDS Aurora, EKS/Bottlerocket, Okta/Auth0, KMS AES-256, expurgo RAM 0s,
  LGPD Art. 11 II g, Parecer Machado Meyer, revogação em 2h, revisão de acesso 6/6 meses, CIS Benchmarks,
  PR com 1 revisor. Isso é adequação real ao projeto.
- **Proporcionais:** 42–98 linhas (mediana 55). Right-sized para uma SaaS de biometria — sem
  enterprise-boilerplate inflado e sem stubs vazios. Têm controle de documento, objetivo, diretrizes
  específicas, revisão e assinatura eletrônica com hash.
- **Consolidação inteligente:** políticas cobrem múltiplos controles (ex.: POL-ACP-001 cobre
  A.5.15/16/17/18 + A.8.3/8.4), o que explica "37 arquivos para 93 controles".

## Defeitos reais encontrados (a corrigir)

1. **Mapa controle→política incorreto (crítico):** `POLICIES/A.8.24.md` (slot de **Uso de Criptografia**)
   contém, na verdade, o **`SOP-HDN-001 Manual de Hardening`, referenciando o controle A.8.9** (Gestão de
   Configuração). Ou seja, **não há política dedicada de Criptografia** para A.8.24; o arquivo foi
   mismapeado. (Confirma o achado F8.)
2. **Papéis inconsistentes:** A.5.15 chama Humberto Oliveira de **"CPO / Diretoria de Identidade"**;
   noutros pontos ele é **"CISO"**. E o contato do DPO é `dpo@twyn.com` na POL-DPP-001 mas `privacy@t4isb.com`
   na ROPA/README. (Reforça NC-08.)
3. **Versão desatualizada:** POL-DPP-001 referencia **27701:2019** — atualizar para **2025** (F7).
4. **Cobertura a confirmar:** as políticas presentes são boas, mas é preciso verificar se **todos** os
   controles aplicáveis têm política/So P vinculada (p.ex. A.8.12 DLP, A.8.23 Filtragem Web parecem sem
   política dedicada).

## Conclusão
A **qualidade de redação e a adequação ao projeto são boas** — não é preciso reescrever a suíte. O
trabalho necessário é de **correção de mapeamento, consistência de papéis, atualização de versão e
fechamento de lacunas pontuais** — não de reconstrução.
