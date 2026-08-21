---
name: consultas-mcp
description: Skill da REST API do Consultas na MCP.AI: 23 endpoints em /api/consultas. Consultas em fontes oficiais sobre pessoas e empresas: situação cadastral (CPF/CNPJ), Simples/MEI, SINTEGRA, certidões (CND Federal, CNDT, FGTS), TCU, sanções (OFAC/ONU/ICIJ) e NF-e. Hospedado pela plataforma, sem credenciais, pague por consulta com crédito pré-pago. Autentique com workspace API key (sk_live) gerada em app.mcp.ai/settings/api-keys. Use quando o usuário pedir algo coberto pelos endpoints.
---

# Consultas — REST API skill

Você tem acesso à **Consultas** REST API na MCP.AI.

> Consultas em fontes oficiais sobre pessoas e empresas: situação cadastral (CPF/CNPJ), Simples/MEI, SINTEGRA, certidões (CND Federal, CNDT, FGTS), TCU, sanções (OFAC/ONU/ICIJ) e NF-e. Hospedado pela plataforma, sem credenciais, pague por consulta com crédito pré-pago.

## Base URL

```
https://api.mcp.ai/api/consultas
```

Todo endpoint é um **POST** na Base URL + o path abaixo. Os parâmetros vão no corpo JSON.

## Autenticação

Inclua em toda request:

```
Authorization: Bearer sk_live_...
Content-Type: application/json
```

> Gere sua chave em **https://app.mcp.ai/settings/api-keys** (workspace API key `sk_live_…`, não expira, revogável). Uma única chave serve pra todos os seus MCPs.

## Formato de resposta

```json
{ "ok": true, "tool": "<tool_id>", "result": <payload> }
```

## Exemplo cURL

```bash
curl -X POST https://api.mcp.ai/api/consultas/antecedentes/sp \
  -H "Authorization: Bearer sk_live_..." \
  -H "Content-Type: application/json" \
  -d '{"nome":"...","birthdate":"...","genero":"..."}'
```

## Reportar problemas

Se um endpoint retornar erro, vazio ou dado inesperado, reporte (não desista calado): **POST /api/consultas/report** com `{ "message": "...", "context"?: "...", "conversation"?: [...] }`. Isso notifica o time da MCP.AI.

## Endpoints (23)

#### `consultas_antecedentes_sp`

Certidão de antecedentes criminais do estado de SP por nome. _(POST /api/consultas/antecedentes/sp)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `nome` | string | Sim | Nome completo. |
| `birthdate` | string | Sim | Data de nascimento (DD/MM/AAAA). |
| `genero` | string | Sim | Gênero (M/F). |

#### `consultas_bcb_valores_receber`

Valores a Receber no Banco Central (SVR) — verifica se uma pessoa ou empresa tem dinheiro esquecido a resgatar. _(POST /api/consultas/bcb/valores/receber)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `cpf` | string | Não | CPF do titular (pessoa física). Use cpf+data_nascimento OU cnpj+data_abertura_empresa. |
| `data_nascimento` | string | Não | Data de nascimento do titular PF (DD/MM/AAAA). Necessária junto com cpf. |
| `cnpj` | string | Não | CNPJ do titular (pessoa jurídica). |
| `data_abertura_empresa` | string | Não | Data de abertura da empresa PJ (DD/MM/AAAA). Necessária junto com cnpj. |

#### `consultas_cnd_estadual`

Certidão Negativa de Débitos Estaduais (CND estadual) de um estado, por CNPJ/CPF/IE. _(POST /api/consultas/cnd/estadual)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `uf` | string | Sim | Sigla do estado (ex.: SP, MG, RJ). |
| `cnpj` | string | Não | CNPJ (informe cnpj, cpf ou ie). |
| `cpf` | string | Não | CPF (informe cnpj, cpf ou ie). |
| `ie` | string | Não | Inscrição Estadual (informe cnpj, cpf ou ie). |

#### `consultas_cnd_federal`

Certidão de débitos federais e Dívida Ativa da União (CND Federal/PGFN) por CNPJ ou CPF. _(POST /api/consultas/cnd/federal)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `cnpj` | string | Não | CNPJ (informe cnpj OU cpf). |
| `cpf` | string | Não | CPF (informe cnpj OU cpf). |

#### `consultas_cndt`

Certidão Negativa de Débitos Trabalhistas (CNDT) por CNPJ ou CPF. _(POST /api/consultas/cndt)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `cnpj` | string | Não | CNPJ (informe cnpj OU cpf). |
| `cpf` | string | Não | CPF (informe cnpj OU cpf). |

#### `consultas_cpf`

Situação cadastral de um CPF na Receita (nome, situação, nascimento, inscrição, óbito). _(POST /api/consultas/cpf)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `cpf` | string | Sim | CPF (só números ou formatado). |
| `birthdate` | string | Sim | Data de nascimento (DD/MM/AAAA). |

#### `consultas_fgts`

Regularidade do empregador perante o FGTS (Certificado de Regularidade — CRF) por CNPJ. _(POST /api/consultas/fgts)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `cnpj` | string | Sim | CNPJ do empregador. |

#### `consultas_irpf`

Comprovante/situação da Declaração de IRPF de um CPF, por ano-calendário. _(POST /api/consultas/irpf)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `cpf` | string | Sim | CPF do declarante. |
| `birthdate` | string | Sim | Data de nascimento (DD/MM/AAAA). |
| `year` | string | Sim | Ano-calendário (ex.: 2025). |

#### `consultas_marcas`

Marcas registradas no INPI por titular (CPF ou CNPJ). _(POST /api/consultas/marcas)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `cnpj` | string | Não | CNPJ do titular (informe cnpj OU cpf). |
| `cpf` | string | Não | CPF do titular (informe cnpj OU cpf). |

#### `consultas_marcas_busca`

Busca marcas no INPI pelo nome/termo (anterioridade/colidência). _(POST /api/consultas/marcas/busca)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `marca` | string | Sim | Nome/termo da marca a buscar. |
| `ncl` | string | Não | Classe de Nice (NCL), ex.: 35. Opcional, restringe a busca à classe. |
| `pesquisa_textual` | string | Não | Tipo de pesquisa textual: exata ou radical (raiz do termo). Opcional. |
| `pedidos_vivos` | string | Não | Restringe a processos vivos (não extintos/arquivados). Opcional. |
| `tipo` | string | Não | Tipo de busca/apresentação da marca. Opcional. |
| `pagina` | string | Não | Página de resultados (paginação). Opcional. |

#### `consultas_marcas_processo`

Detalhes completos de um processo de registro de marca no INPI pelo número do processo (situação, depósito, concessão, vigência, titulares, classes Nice/Viena, petições, publicações). _(POST /api/consultas/marcas/processo)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `numero_processo` | string | Sim | Número do processo da marca no INPI. |

#### `consultas_mei`

Dados do MEI (Microempreendedor Individual) por CPF ou CNPJ. _(POST /api/consultas/mei)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `cnpj` | string | Não | CNPJ do MEI (informe cnpj OU cpf). |
| `cpf` | string | Não | CPF do empreendedor (informe cnpj OU cpf). |

#### `consultas_nfe`

Consulta uma Nota Fiscal Eletrônica (NF-e) pela chave de acesso (44 dígitos). _(POST /api/consultas/nfe)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `nfe` | string | Sim | Chave de acesso da NF-e (44 dígitos). |

#### `consultas_offshore_leaks`

Busca na base ICIJ Offshore Leaks (paraísos fiscais) por nome/termo. _(POST /api/consultas/offshore/leaks)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `query` | string | Sim | Nome ou termo a buscar. |

#### `consultas_patentes`

Patentes registradas no INPI por titular (CPF ou CNPJ). _(POST /api/consultas/patentes)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `cnpj` | string | Não | CNPJ do titular (informe cnpj OU cpf). |
| `cpf` | string | Não | CPF do titular (informe cnpj OU cpf). |

#### `consultas_sancoes_ofac`

Busca em listas de sanções do OFAC (EUA) por nome/termo. _(POST /api/consultas/sancoes/ofac)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `query` | string | Sim | Nome ou termo a buscar. |

#### `consultas_sancoes_onu`

Busca em listas de sanções da ONU por nome/termo. _(POST /api/consultas/sancoes/onu)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `query` | string | Sim | Nome ou termo a buscar. |

#### `consultas_seeu_processos`

Processos de execução penal no SEEU (Sistema Eletrônico de Execução Unificado do CNJ) por CPF, CNPJ, nome da parte ou número de processo. _(POST /api/consultas/seeu/processos)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `cpf` | string | Não | CPF da parte. |
| `cnpj` | string | Não | CNPJ da parte. |
| `nome_parte` | string | Não | Nome da parte (use nome_mae para desambiguar homônimos). |
| `nome_mae` | string | Não | Nome da mãe da parte. |
| `numero_processo` | string | Não | Número único do processo (padrão CNJ). |

#### `consultas_simples`

Situação no Simples Nacional / SIMEI de um CNPJ. _(POST /api/consultas/simples)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `cnpj` | string | Sim | CNPJ. |

#### `consultas_sintegra_rj`

Situação cadastral de ICMS (SINTEGRA) no estado do RJ por CNPJ ou CPF. _(POST /api/consultas/sintegra/rj)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `cnpj` | string | Não | CNPJ (informe cnpj OU cpf). |
| `cpf` | string | Não | CPF (informe cnpj OU cpf). |

#### `consultas_sintegra_sp`

Situação cadastral de ICMS (SINTEGRA) no estado de SP por CNPJ ou CPF. _(POST /api/consultas/sintegra/sp)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `cnpj` | string | Não | CNPJ (informe cnpj OU cpf). |
| `cpf` | string | Não | CPF (informe cnpj OU cpf). |

#### `consultas_sintegra_suframa`

Situação cadastral na SUFRAMA por CNPJ ou CPF. _(POST /api/consultas/sintegra/suframa)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `cnpj` | string | Não | CNPJ (informe cnpj OU cpf). |
| `cpf` | string | Não | CPF (informe cnpj OU cpf). |

#### `consultas_tcu_pj`

Consulta consolidada do TCU para uma PJ (inidôneos, inabilitados, contas irregulares) por CNPJ. _(POST /api/consultas/tcu/pj)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `cnpj` | string | Sim | CNPJ. |

---

Este MCP também funciona via **conexão MCP** (Claude / Cursor) em `https://api.mcp.ai/p_consultas` — veja o [README](../../README.md). A skill acima é pra consumir a **REST API** direto (agente próprio / código).
