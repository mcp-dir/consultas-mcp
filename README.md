# Consultas

### Consultas para Claude, ChatGPT e agentes de IA

Consultas em fontes oficiais sobre pessoas e empresas: situação cadastral (CPF/CNPJ), Simples/MEI, SINTEGRA, certidões (CND Federal, CNDT, FGTS), TCU, sanções (OFAC/ONU/ICIJ) e NF-e. Hospedado pela plataforma, sem credenciais, pague por consulta com crédito pré-pago.

- 📊 **23 ferramentas**
- 🔒 **Somente leitura**
- 💬 **Funciona com qualquer cliente MCP**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Login via magic-link (sem senha)**

[English version](README.en.md) · [Documentação completa](docs/) · [Skill pra agentes](skills/)

---

## Instalar em 1 clique

### Claude (Web e Desktop)

A Anthropic unificou a instalação de MCPs em `claude.ai/customize/connectors`. **O mesmo link serve pra Claude Web e Claude Desktop** (basta estar logado):

[➕ Abrir no Claude e conectar](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

**Manual** (se o deeplink não abrir): [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Adicionar conector personalizado** → cole **Nome** `Consultas` e **URL** `https://api.mcp.ai/p_consultas`.

### Cursor

[➕ Instalar Consultas no Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=consultas&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9jb25zdWx0YXMifQ==)

### VS Code (Copilot Chat)

[➕ Instalar Consultas no VS Code](vscode:mcp/install?name=consultas&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_consultas%22%7D)

### ChatGPT, Manus, OpenClaw e mais 40+ clientes

Funciona em qualquer cliente MCP que suporte **MCP over HTTP**. A URL do servidor é sempre:

```
https://api.mcp.ai/p_consultas
```

Detalhes por cliente: [INSTALL.md](INSTALL.md).

---

## Exemplos de uso

```
Esse CNPJ tem CND Federal negativa e CNDT?
Situação cadastral do CPF 000.000.000-00 (nascido em 01/01/1990)?
Esse nome aparece em listas de sanções (OFAC/ONU)?
```

---

## 23 ferramentas disponíveis

| Tool | Descrição |
|---|---|
| `consultas_cpf` | Situação cadastral de um CPF na Receita (nome, situação, nascimento, inscrição, óbito). |
| `consultas_irpf` | Comprovante/situação da Declaração de IRPF de um CPF, por ano-calendário. |
| `consultas_antecedentes_sp` | Certidão de antecedentes criminais do estado de SP por nome. |
| `consultas_seeu_processos` | Processos de execução penal no SEEU (Sistema Eletrônico de Execução Unificado do CNJ) por CPF, CNPJ, nome da parte ou número de processo. |
| `consultas_simples` | Situação no Simples Nacional / SIMEI de um CNPJ. |
| `consultas_mei` | Dados do MEI (Microempreendedor Individual) por CPF ou CNPJ. |
| `consultas_sintegra_sp` | Situação cadastral de ICMS (SINTEGRA) no estado de SP por CNPJ ou CPF. |
| `consultas_sintegra_rj` | Situação cadastral de ICMS (SINTEGRA) no estado do RJ por CNPJ ou CPF. |
| `consultas_sintegra_suframa` | Situação cadastral na SUFRAMA por CNPJ ou CPF. |
| `consultas_tcu_pj` | Consulta consolidada do TCU para uma PJ (inidôneos, inabilitados, contas irregulares) por CNPJ. |
| `consultas_cnd_federal` | Certidão de débitos federais e Dívida Ativa da União (CND Federal/PGFN) por CNPJ ou CPF. |
| `consultas_cndt` | Certidão Negativa de Débitos Trabalhistas (CNDT) por CNPJ ou CPF. |
| `consultas_fgts` | Regularidade do empregador perante o FGTS (Certificado de Regularidade — CRF) por CNPJ. |
| `consultas_cnd_estadual` | Certidão Negativa de Débitos Estaduais (CND estadual) de um estado, por CNPJ/CPF/IE. |
| `consultas_sancoes_ofac` | Busca em listas de sanções do OFAC (EUA) por nome/termo. |
| `consultas_sancoes_onu` | Busca em listas de sanções da ONU por nome/termo. |
| `consultas_offshore_leaks` | Busca na base ICIJ Offshore Leaks (paraísos fiscais) por nome/termo. |
| `consultas_marcas` | Marcas registradas no INPI por titular (CPF ou CNPJ). |
| `consultas_marcas_busca` | Busca marcas no INPI pelo nome/termo (anterioridade/colidência). |
| `consultas_marcas_processo` | Detalhes completos de um processo de registro de marca no INPI pelo número do processo (situação, depósito, concessão, vigência, titulares, classes Nice/Viena, petições, publicações). |
| `consultas_patentes` | Patentes registradas no INPI por titular (CPF ou CNPJ). |
| `consultas_nfe` | Consulta uma Nota Fiscal Eletrônica (NF-e) pela chave de acesso (44 dígitos). |
| `consultas_bcb_valores_receber` | Valores a Receber no Banco Central (SVR) — verifica se uma pessoa ou empresa tem dinheiro esquecido a resgatar. |

Detalhe de cada tool: [docs/ferramentas.md](docs/ferramentas.md)

---

## Preços

Pré-pago (carteira de créditos), paga por uso. Veja [docs/precos.md](docs/precos.md).

---

## Privacidade & LGPD

- **Somente leitura**, nenhuma ferramenta altera dados na origem.
- **Sub-processadores**: o LLM host que você escolher (Claude, ChatGPT, Cursor, agente próprio). Lista completa em [docs/privacidade-lgpd.md](docs/privacidade-lgpd.md).
- Os dados retornados pelas tools são enviados ao **LLM host que você escolher**, sub-processador fora do nosso controle. Recomendamos planos com opt-out de treinamento.

---

## Perguntas frequentes

**O servidor é open source?**
O servidor é proprietário (hosted). Este repositório é o wrapper público com manifestos, docs e skills — tudo MIT.

**Posso usar com agente próprio (não Claude/Cursor)?**
Sim — qualquer cliente que suporte MCP over HTTP. URL: `https://api.mcp.ai/p_consultas`.


---

## Suporte

- 📧 [consultas@mcp.ai](mailto:consultas@mcp.ai)
- 🐛 [GitHub Issues](https://github.com/mcp-dir/consultas-mcp/issues)
- 📄 [docs/](docs/)

---

## Licença

MIT — veja [LICENSE](LICENSE). O servidor MCP em `api.mcp.ai/p_consultas` é proprietário (hosted); este repositório (manifestos, docs, skills) é MIT.
