# 🔌 Serverest API Testing | Postman

<p align="center">
  <strong>Projeto de portfólio para prática de testes de API REST com Postman e JavaScript.</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/QA-API%20Testing-6A5ACD?style=for-the-badge" alt="QA API Testing">
  <img src="https://img.shields.io/badge/Tool-Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white" alt="Postman">
  <img src="https://img.shields.io/badge/Language-JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript">
  <img src="https://img.shields.io/badge/API-REST-2563EB?style=for-the-badge" alt="REST API">
</p>

> **Objetivo:** demonstrar como estruturo e valido fluxos de API usando assertions, variáveis, autenticação, dados retornados entre requisições e verificações de regras de negócio. Este é um projeto de estudo e portfólio, não um sistema de produção.

## 📌 Visão geral

A coleção utiliza a [Serverest](https://serverest.dev/) como API de prática. Os testes verificam respostas HTTP, mensagens, campos de resposta e regras de negócio em fluxos de usuários, produtos e carrinhos.

### O que este projeto demonstra

- Validação de códigos HTTP e conteúdo da resposta.
- Assertions com JavaScript na aba **Scripts → After response**.
- Uso de variáveis de ambiente, incluindo `baseURL`, `accessToken`, `newProductId` e `carrinhoId`.
- Autenticação por Bearer Token em rotas protegidas.
- Reutilização de IDs retornados por requisições anteriores.
- Validação de regras de negócio, como restrições de carrinho e produtos duplicados.
- Cálculo dinâmico do preço total e da quantidade total do carrinho a partir dos produtos retornados.

## 🧪 Fluxos explorados

| Área | Requisições / comportamentos |
|---|---|
| Autenticação | Login e uso do token em requisições protegidas |
| Usuários | Cadastro, consulta, listagem, edição e exclusão na coleção |
| Produtos | Cadastro, consulta por ID, listagem, edição e exclusão na coleção |
| Carrinhos | Cadastro, consulta por ID, conclusão de compra e cancelamento com retorno ao estoque |

> A tabela descreve os fluxos presentes na coleção. A cobertura de assertions e a execução automatizada são ampliadas de forma incremental; consulte os scripts e os resultados no Postman para verificar o estado mais recente de cada requisição.

## 🔍 Exemplos de validação

### Cadastro de carrinho

O teste de cadastro verifica o status esperado, a mensagem da API e a presença do identificador. Quando a API confirma o cadastro com status `201`, o script salva o `_id` retornado na variável de ambiente `carrinhoId`.

### Consulta do carrinho

A consulta usa a URL dinâmica:

```text
{{baseURL}}/carrinhos/{{carrinhoId}}
```

Os testes verificam o status `200`, a presença de produtos, a consistência dos totais e a existência do ID retornado.

O total é calculado a partir dos dados recebidos, em vez de depender de números fixos:

```javascript
const responseJson = pm.response.json();

const precoTotalCalculado = responseJson.produtos.reduce(
  (total, produto) => total + produto.quantidade * produto.precoUnitario,
  0
);

const quantidadeTotalCalculada = responseJson.produtos.reduce(
  (total, produto) => total + produto.quantidade,
  0
);

pm.expect(responseJson.precoTotal).to.eql(precoTotalCalculado);
pm.expect(responseJson.quantidadeTotal).to.eql(quantidadeTotalCalculada);
```

## 🧰 Tecnologias e conceitos

- **Postman** — organização e execução das requisições.
- **JavaScript** — scripts de validação e manipulação de respostas.
- **HTTP / REST / JSON** — métodos, códigos de status e payloads.
- **Variáveis de ambiente** — configuração reutilizável e encadeamento entre chamadas.
- **Assertions** — validação de comportamento esperado e regras de negócio.
- **Git / GitHub** — versionamento e documentação do projeto.

## 🚀 Como explorar o projeto

1. Acesse a [API Serverest](https://serverest.dev/) e leia a documentação das rotas.
2. No Postman, importe a coleção exportada do workspace do projeto.
3. Crie ou selecione um ambiente para a API.
4. Configure a variável `baseURL` com `https://serverest.dev`.
5. Não publique tokens, senhas ou valores sensíveis no repositório. Gere credenciais de teste próprias e mantenha-as no ambiente local do Postman.
6. Execute primeiro os fluxos de preparação (cadastro/login, conforme necessário) e depois os fluxos que dependem dos IDs retornados.
7. Abra **Test Results** após cada execução para revisar as assertions.

### Variáveis utilizadas

| Variável | Finalidade |
|---|---|
| `baseURL` | URL base da API |
| `email` | E-mail de teste usado no fluxo de autenticação |
| `password` | Senha de teste mantida no ambiente local |
| `accessToken` | Token de autenticação retornado pelo login |
| `newProductId` | ID do produto criado/selecionado para o fluxo |
| `carrinhoId` | ID do carrinho retornado pelo cadastro |

Os valores devem ser preenchidos ou gerados durante a execução. **Não compartilhe um arquivo de ambiente com credenciais ou tokens reais.**

## ⚠️ Comportamentos importantes da API de estudo

- Os dados da Serverest podem expirar ou ser removidos, então pode ser necessário cadastrar o usuário e os dados novamente antes de executar os fluxos.
- A API permite apenas um carrinho ativo por usuário; criar outro carrinho sem concluir ou cancelar o atual pode retornar erro.
- Um carrinho não pode conter o mesmo produto duplicado em entradas separadas.
- Requisições de conclusão e cancelamento alteram o estado do carrinho. Execute-as somente quando houver um carrinho de teste ativo.
- Uma resposta de erro pode ser um resultado esperado em um cenário negativo; avalie status, mensagem e regra de negócio em conjunto.

## 🗺️ Próximas melhorias

- [ ] Versionar no repositório o arquivo exportado da coleção Postman, sem segredos.
- [ ] Documentar cada cenário com pré-condições, passos e resultado esperado.
- [ ] Expandir cenários negativos e validações de contrato.
- [ ] Tornar os dados de teste mais independentes e repetíveis.
- [ ] Executar a coleção pela linha de comando usando Newman.
- [ ] Integrar a execução ao GitHub Actions depois de validar o fluxo local.
- [ ] Publicar evidências e relatórios reais das execuções.

## 👨‍💻 Autor

**Lucas Estevam** — QA / Testes de Software e Automação

- [GitHub](https://github.com/Estevam98)
- [LinkedIn](https://www.linkedin.com/in/lucasestevam-qa/)

---

*Projeto educacional em evolução contínua. As próximas etapas serão registradas à medida que forem implementadas e validadas.*
