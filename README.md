# 🔌 Serverest API Testing

> Projeto de testes de API desenvolvido com Postman para validação de uma API REST, utilizando cenários funcionais, assertions, dados dinâmicos, autenticação e encadeamento entre requisições.

---

## 🎯 Objetivo

Este projeto foi desenvolvido com o objetivo de praticar e demonstrar conhecimentos em testes de API utilizando Postman.

A estratégia de testes contempla validações de endpoints, códigos HTTP, tempo de resposta, autenticação, criação de dados dinâmicos e utilização de informações retornadas por uma requisição em requisições posteriores.

O projeto utiliza a API Serverest como ambiente de estudo.

---

## 🛠️ Tecnologias

- Postman
- JavaScript
- JSON
- REST API
- HTTP
- Git
- GitHub

---

## 🧪 Cobertura de testes

A collection está organizada nos seguintes módulos:

### 🔐 Login

- Realizar login

### 👤 Usuário

- Buscar usuário por ID
- Listar usuários cadastrados
- Cadastrar usuário
- Editar usuário
- Excluir usuário

### 📦 Produtos

- Cadastrar produto
- Listar produtos cadastrados
- Buscar produto por ID
- Editar produto
- Excluir produto

### 🛒 Carrinho

- Listar carrinhos cadastrados
- Cadastrar carrinho
- Buscar carrinho por ID
- Excluir carrinho
- Excluir carrinho e retornar produtos para estoque

---

## ⚙️ Automações implementadas

### Dados dinâmicos

Na criação de usuários são utilizados dados dinâmicos para evitar a utilização repetida dos mesmos valores.

Exemplo:

```javascript
const randomNumber = Math.floor(Math.random() * 9000)
const randomName = `User Number ${randomNumber}`
const randomEmail = `name.${randomNumber}@qa.com`

pm.globals.set('email', randomEmail)
pm.globals.set('user', randomName)
