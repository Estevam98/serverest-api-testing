# 🔌 Serverest API Testing | Postman

Projeto de portfólio para praticar testes de API REST usando Postman, JavaScript e a API Serverest.

## Objetivo

Demonstrar a criação e execução de requisições de API, validação de respostas HTTP, assertions, autenticação e reutilização de dados entre chamadas.

## Cenários incluídos

- **Login:** validação da resposta e armazenamento do token.
- **Usuários:** cadastro com dados dinâmicos, consulta, edição e exclusão.
- **Produtos:** cadastro, listagem, consulta, edição e exclusão.
- **Carrinhos:** cadastro, consulta, validação de totais, conclusão de compra e cancelamento.

## Tecnologias

- Postman
- JavaScript para scripts e assertions
- HTTP, REST e JSON
- Variáveis de ambiente
- Git e GitHub

## Como executar

1. Importe `Postman/Serverest.postman_collection.json` no Postman.
2. Crie e selecione um ambiente.
3. Configure `baseURL` como `https://serverest.dev`.
4. Execute **Cadastrar usuário** para gerar `nome`, `email`, `password` e `newUserId`.
5. Execute **Realizar login** para gerar `accessToken`.
6. Execute o cadastro de produto antes de consultas, edição ou carrinho para preencher `newProductId`.
7. Execute o cadastro de carrinho antes da consulta para preencher `carrinhoId`.
8. Confira os resultados na aba **Test Results**.

## Variáveis usadas

| Variável | Finalidade |
|---|---|
| `baseURL` | Endereço base da API |
| `nome`, `email`, `password` | Dados gerados no cadastro do usuário |
| `newUserId` | ID retornado pelo cadastro do usuário |
| `accessToken` | Token retornado pelo login |
| `randomProduct` | Nome dinâmico do produto |
| `newProductId` | ID retornado pelo cadastro do produto |
| `carrinhoId` | ID retornado pelo cadastro do carrinho |

## Observações

- Execute as requisições na ordem adequada, pois algumas dependem de IDs e tokens gerados por requisições anteriores.
- A API de estudo pode remover dados; cadastre novamente os recursos quando necessário.
- Concluir ou cancelar uma compra altera o estado do carrinho.
- Este é um projeto de estudo. Os testes precisam ser executados no Postman para confirmar os resultados; a publicação do código, por si só, não comprova que todos passaram.

## Próximas melhorias

- [ ] Executar e revisar todos os cenários no Postman.
- [ ] Expandir cenários negativos e validações de contrato.
- [ ] Executar a coleção com Newman.
- [ ] Integrar a execução validada ao GitHub Actions.

## Autor

**Lucas Estevam** — QA / Testes de Software e Automação

- [GitHub](https://github.com/Estevam98)
- [LinkedIn](https://www.linkedin.com/in/lucasestevam-qa/)
