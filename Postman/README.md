# 📮 Coleção Postman — Serverest

Esta pasta contém a coleção usada para praticar testes de API REST na Serverest.

## Arquivo

- `Serverest.postman_collection.json` — coleção de requisições e testes automatizados.

## Importação e execução

1. No Postman, selecione **Import** e escolha o arquivo JSON desta pasta.
2. Crie um ambiente com `baseURL = https://serverest.dev`.
3. Execute **Cadastrar usuário** e depois **Realizar login**.
4. Cadastre um produto antes de executar as requisições que usam `newProductId`.
5. Cadastre um carrinho antes de executar a consulta com `carrinhoId`.
6. Confira os resultados em **Test Results**.

A coleção gera IDs e dados de teste durante a execução. Não adicione tokens ou credenciais pessoais ao repositório. Como a API de estudo pode remover dados, pode ser necessário recriar os recursos.

Consulte o [README principal](../README.md) para a visão geral do projeto.
