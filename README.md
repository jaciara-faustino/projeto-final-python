# Projeto de Extração e Armazenamento de Dados da Brasil API

Este projeto demonstra como extrair dados de diversas APIs fornecidas pelo Brasil API, processar esses dados e armazená-los em um banco de dados SQLite.

## Sumário

1. [Visão Geral](#visão-geral)
2. [Requisitos](#requisitos)
3. [Descrição das Funções](#descrição-das-funções)


## Visão Geral

O objetivo deste projeto é buscar informações de três fontes diferentes:

[API de Estados IBGE](https://brasilapi.com.br/api/ibge/uf/v1) : Fornece informações sobre estados Provenientes do IBGE.

[API de Corretoras](https://brasilapi.com.br/api/cvm/corretoras/v1): Fornece informações referentes a Corretoras ativas listadas na CVM.

[API de Taxas](https://brasilapi.com.br/api/taxas/v1): Fornece informações sobre taxas de juros as taxas de juros e alguns índices oficiais do Brasil.

Esses dados são então processados e salvos em um banco de dados SQLite para posterior análise.

## Criação de Alerta de Erro

Nesta etapa, o objetivo é garantir que o código seja capaz de detectar e lidar com erros que possam ocorrer durante a execução. Um exemplo comum é a tentativa de acessar uma API ou abrir um arquivo, onde podem ocorrer problemas como falha na conexão ou ausência do arquivo.

## Requisitos

Certifique-se de ter as seguintes bibliotecas instaladas:

- `pandas`
- `requests`
- `sqlite3` 
- `plyer` (para notificações)

Você pode instalar as bibliotecas necessárias usando o `pip`:

## Descrição das Funções

### estados_ibge()
Esta função faz uma requisição para a API de Estados do Brasil e retorna um DataFrame com as seguintes informações:

- Sigla do estado (UF)
- Nome do estado (Estado)
- Região (Regiao)

### taxas_juros()
Esta função obtém as taxas de juros atuais e retorna um DataFrame com as seguintes informações:

Nome da taxa (Nome da Taxa)
Valor da taxa em porcentagem (Taxa de Juros (%))
Colunas não relevantes são removidas.

### corretoras()
Esta função busca informações sobre corretoras e retorna um DataFrame com:

Código CVM (Código CVM)
Nome Social (Nome Social)
Nome Comercial (Nome Comercial)
CNPJ (CNPJ)

### salvar_bd(df, tabela_nome, conexao)
Esta função salva um DataFrame em uma tabela no banco de dados SQLite.

