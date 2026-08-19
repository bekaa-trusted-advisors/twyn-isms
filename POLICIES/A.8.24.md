# POL-CRY-001: Política de Criptografia e Gestão de Chaves — TWYN Face ID Platform
**ISO/IEC 27001:2022 Controle A.8.24 (Uso de criptografia)**

---

**Controle de Documento**

| Campo | Valor |
|-------|-------|
| **Document ID** | POL-CRY-001 |
| **Version** | 1.0 (Rascunho) |
| **Autor** | Consultoria Aegis (ENG-2026-001) |
| **Aprovador** | _Pendente — CTO / CEO_ |
| **Data de Emissão** | _Pendente de aprovação_ |
| **Status** | `Rascunho — aguarda aprovação` |

> Substitui o conteúdo anterior deste arquivo, que era o `SOP-HDN-001 (Hardening / A.8.9)` mismapeado ao
> controle A.8.24. O Hardening permanece em `POLICIES/A.8.9.md`. Corrige o achado F8 / issue #12.

---

## 1. Objetivo

Estabelecer as regras de uso de criptografia e gestão do ciclo de vida de chaves na TWYN Face ID
Platform, garantindo a proteção de dados pessoais sensíveis (vetores biométricos) e de credenciais em
repouso e em trânsito, em conformidade com a LGPD e a ISO/IEC 27001:2022 (A.8.24).

## 2. Criptografia em Repouso (at rest)

1.  **Padrão mínimo:** `AES-256`. Todos os volumes do banco RDS Aurora, snapshots, volumes EBS e buckets
    de logs de produção devem estar criptografados em repouso.
2.  **Vetores biométricos:** o vetor matemático (template facial) armazenado no RDS deve ser cifrado sob
    chave dedicada do **AWS KMS**, distinta das chaves de uso geral.
3.  **Chaves gerenciadas pelo cliente (CMK):** usar chaves do KMS de titularidade da TWYN (não chaves
    padrão do serviço) para os dados sensíveis, permitindo rotação e revogação controladas.

## 3. Criptografia em Trânsito (in transit)

1.  **TLS 1.2+ (preferencialmente 1.3):** toda a comunicação da API pública e entre serviços internos
    deve usar TLS; conexões em texto claro são proibidas.
2.  **Sem downgrade:** desabilitar suites e protocolos obsoletos (SSLv3, TLS 1.0/1.1).

## 4. Gestão do Ciclo de Vida de Chaves

1.  **Custódia:** as chaves mestras residem no AWS KMS; material de chave não é exportado em texto claro.
2.  **Rotação:** habilitar rotação automática anual das CMK do KMS; rotação imediata sob suspeita de
    comprometimento.
3.  **Segregação de funções:** quem administra chaves não deve ser o mesmo que administra os dados por
    elas protegidos (alinhado a A.5.3).
4.  **Segredos de aplicação:** proibida a gravação de segredos/senhas em texto claro no código ou em
    variáveis de ambiente versionadas; usar **AWS Secrets Manager / 1Password**.

## 5. Governança

1.  Exceções a esta política exigem aprovação formal do CTO e registro de risco.
2.  A conformidade é evidenciada por: config do KMS (rotação/políticas de chave), config de criptografia
    do RDS/EBS/S3, e políticas de TLS dos endpoints. (Ver export em issue #9.)

## 6. Revisão e Aprovação

Política a ser aprovada pela Liderança Técnica (CTO) e Diretoria Executiva (CEO) e revisada anualmente.

> **Assinatura eletrônica:** _pendente de aprovação formal no nISO / TWYN GRC Portal._
