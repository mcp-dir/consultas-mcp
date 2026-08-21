# Ferramentas

Consultas expõe 23 ferramentas (todas somente leitura).

### 1. `consultas_cpf`
**Input**: `cpf`, `birthdate`

Situação cadastral de um CPF na Receita (nome, situação, nascimento, inscrição, óbito).

### 2. `consultas_irpf`
**Input**: `cpf`, `birthdate`, `year`

Comprovante/situação da Declaração de IRPF de um CPF, por ano-calendário.

### 3. `consultas_antecedentes_sp`
**Input**: `nome`, `birthdate`, `genero`

Certidão de antecedentes criminais do estado de SP por nome.

### 4. `consultas_seeu_processos`
**Input**: `cpf` (opcional), `cnpj` (opcional), `nome_parte` (opcional), `nome_mae` (opcional), `numero_processo` (opcional)

Processos de execução penal no SEEU (Sistema Eletrônico de Execução Unificado do CNJ) por CPF, CNPJ, nome da parte ou número de processo.

### 5. `consultas_simples`
**Input**: `cnpj`

Situação no Simples Nacional / SIMEI de um CNPJ.

### 6. `consultas_mei`
**Input**: `cnpj` (opcional), `cpf` (opcional)

Dados do MEI (Microempreendedor Individual) por CPF ou CNPJ.

### 7. `consultas_sintegra_sp`
**Input**: `cnpj` (opcional), `cpf` (opcional)

Situação cadastral de ICMS (SINTEGRA) no estado de SP por CNPJ ou CPF.

### 8. `consultas_sintegra_rj`
**Input**: `cnpj` (opcional), `cpf` (opcional)

Situação cadastral de ICMS (SINTEGRA) no estado do RJ por CNPJ ou CPF.

### 9. `consultas_sintegra_suframa`
**Input**: `cnpj` (opcional), `cpf` (opcional)

Situação cadastral na SUFRAMA por CNPJ ou CPF.

### 10. `consultas_tcu_pj`
**Input**: `cnpj`

Consulta consolidada do TCU para uma PJ (inidôneos, inabilitados, contas irregulares) por CNPJ.

### 11. `consultas_cnd_federal`
**Input**: `cnpj` (opcional), `cpf` (opcional)

Certidão de débitos federais e Dívida Ativa da União (CND Federal/PGFN) por CNPJ ou CPF.

### 12. `consultas_cndt`
**Input**: `cnpj` (opcional), `cpf` (opcional)

Certidão Negativa de Débitos Trabalhistas (CNDT) por CNPJ ou CPF.

### 13. `consultas_fgts`
**Input**: `cnpj`

Regularidade do empregador perante o FGTS (Certificado de Regularidade — CRF) por CNPJ.

### 14. `consultas_cnd_estadual`
**Input**: `uf`, `cnpj` (opcional), `cpf` (opcional), `ie` (opcional)

Certidão Negativa de Débitos Estaduais (CND estadual) de um estado, por CNPJ/CPF/IE.

### 15. `consultas_sancoes_ofac`
**Input**: `query`

Busca em listas de sanções do OFAC (EUA) por nome/termo.

### 16. `consultas_sancoes_onu`
**Input**: `query`

Busca em listas de sanções da ONU por nome/termo.

### 17. `consultas_offshore_leaks`
**Input**: `query`

Busca na base ICIJ Offshore Leaks (paraísos fiscais) por nome/termo.

### 18. `consultas_marcas`
**Input**: `cnpj` (opcional), `cpf` (opcional)

Marcas registradas no INPI por titular (CPF ou CNPJ).

### 19. `consultas_marcas_busca`
**Input**: `marca`, `ncl` (opcional), `pesquisa_textual` (opcional), `pedidos_vivos` (opcional), `tipo` (opcional), `pagina` (opcional)

Busca marcas no INPI pelo nome/termo (anterioridade/colidência).

### 20. `consultas_marcas_processo`
**Input**: `numero_processo`

Detalhes completos de um processo de registro de marca no INPI pelo número do processo (situação, depósito, concessão, vigência, titulares, classes Nice/Viena, petições, publicações).

### 21. `consultas_patentes`
**Input**: `cnpj` (opcional), `cpf` (opcional)

Patentes registradas no INPI por titular (CPF ou CNPJ).

### 22. `consultas_nfe`
**Input**: `nfe`

Consulta uma Nota Fiscal Eletrônica (NF-e) pela chave de acesso (44 dígitos).

### 23. `consultas_bcb_valores_receber`
**Input**: `cpf` (opcional), `data_nascimento` (opcional), `cnpj` (opcional), `data_abertura_empresa` (opcional)

Valores a Receber no Banco Central (SVR) — verifica se uma pessoa ou empresa tem dinheiro esquecido a resgatar.

## Prompts de exemplo

```
Esse CNPJ tem CND Federal negativa e CNDT?
Situação cadastral do CPF 000.000.000-00 (nascido em 01/01/1990)?
Esse nome aparece em listas de sanções (OFAC/ONU)?
```
