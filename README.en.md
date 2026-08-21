# Consultas

### Consultas for Claude, ChatGPT and AI agents

Official-source lookups on people and companies: registration status (CPF/CNPJ), Simples/MEI, SINTEGRA, clearance certificates (Federal CND, CNDT, FGTS), TCU, sanctions (OFAC/UN/ICIJ) and NF-e. Platform-hosted, no credentials, pay per query with prepaid credit.

- 📊 **23 tools**
- 🔒 **Read-only**
- 💬 **Works with any MCP client**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Magic-link login (no password)**

[Portuguese version](README.md) · [Full docs (PT-BR)](docs/)

---

## One-click install

### Claude (Web and Desktop)

[➕ Open in Claude and connect](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

Manual: [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Add custom connector** → name `Consultas`, URL `https://api.mcp.ai/p_consultas`.

### Cursor

[➕ Install in Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=consultas&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9jb25zdWx0YXMifQ==)

### VS Code (Copilot Chat)

[➕ Install in VS Code](vscode:mcp/install?name=consultas&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_consultas%22%7D)

### Any other MCP-over-HTTP client

```
https://api.mcp.ai/p_consultas
```

---

## 23 tools

| Tool | Description |
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

---

## Pricing

See [docs/precos.md](docs/precos.md) (PT-BR).

---

## License

MIT — see [LICENSE](LICENSE). The MCP server at `api.mcp.ai/p_consultas` is proprietary (hosted); this repo (manifests, docs, skills) is MIT.
