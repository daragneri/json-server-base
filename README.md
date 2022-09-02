<h1 align="center">
  SuperDucks - API
</h1>

<p align = "center">
Este é o backend da aplicação SuperDucks, o projeto final de front-end do terceiro módulo da Kenzie - Uma aplicação para encontrar seus filmes favoritos! O objetivo dessa aplicação é conseguir recomendar filmes aos usuários e conecta-los com facilidade as telas.
</p>

Esse é o repositório com a base de JSON-Server + JSON-Server-Auth, feita para ser usada no desenvolvimento da API no Projetos final de Front-end.

## Endpoints

A API tem um total de 7 endpoints, sendo voltada ao usuário - podendo cadastrar seu perfil, listar seus filmes favoritos e lsitar gêneros favoritos. <br/>
O url base da API é https://final-project-m3.herokuapp.com

## Rotas que não precisam de autenticação

<h2 align ='center'> Criação de usuário </h2>

POST /register

```json
{
  "name": "John Doe",
  "email": "johndoe@email.com",
  "password": "123456",
  "genres": [],
  "movie_list": []
}
```

Caso dê tudo certo, a resposta será assim:

```json
{
	"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImpvaG5kb2VAZW1haWwuY29tIiwiaWF0IjoxNjYyMTMzMTM2LCJleHAiOjE2NjIxMzY3MzYsInN1YiI6IjUifQ.qZshpSm-BelAdl0wiv7xbShGFI8mTmnpflnQu1SscLY",
	"user": {
		"email": "johndoe@email.com",
		"name": "John Doe",
		"confirmPassword": "123456",
		"id": 5
		"
	}
}
```

<h2 align ='center'> Possíveis erros </h2>

Caso você acabe errando e mandando algum campo errado, a resposta de erro será assim:

A senha necessita de 4 caracteres.

`POST /register - `
` FORMATO DA RESPOSTA - STATUS 400`

```json
{
  "status": "error",
  "message": ["password: minimum is too short"]
}
```

Email já cadastrado:

`POST /register - `
` FORMATO DA RESPOSTA - STATUS 400`

```json
{
  "status": "error",
  "message": "Email already exists"
}
```

Email com formato errado:

`POST /register - `
` FORMATO DA RESPOSTA - STATUS 400`

```json
{
  "status": "error",
  "message": "Email format is invalid"
}
```

<h2 align = "center"> Login </h2>

`POST /login <br/> FORMATO DA REQUISIÇÃO`

```json
{
  "email": "johndoe@email.com",
  "password": "123456"
}
```

Caso dê tudo certo, a resposta será assim:

`POST /login - FORMATO DA RESPOSTA - STATUS 201`

```json
{
	"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImpvaG5kb2VAZW1haWwuY29tIiwiaWF0IjoxNjYyMTMzMTM2LCJleHAiOjE2NjIxMzY3MzYsInN1YiI6IjUifQ.qZshpSm-BelAdl0wiv7xbShGFI8mTmnpflnQu1SscLY",
	"user": {
		"email": "johndoe@email.com",
		"name": "John Doe",
		"confirmPassword": "123456",
		"id": 5
	}
}
```

## Rotas que necessitam de autorização

Rotas que necessitam de autorização deve ser informado no cabeçalho da requisição o campo "Authorization", dessa forma:

> Authorization: Bearer {token}

`PATCH /users/id - FORMATO DA REQUISIÇÃO`

```json
"genres": ["Drama", "Action"]
```

Nesse endpoint podemos atualizar os genêros selecionados pelo usuário

`PATCH /users/id - FORMATO DA REQUISIÇÃO`

```json
"movies_list": ["Drama", "Action"]
```

Nesse endpoint podemos atualizar a lista de filmes selecionados pelo usuário

`PATCH /users/id - FORMATO DA REQUISIÇÃO`

```json
"name": "John Doe",
```

Nesse endpoint podemos alterar o nome do usuário

`PATCH /users/id - FORMATO DA REQUISIÇÃO`

```json
"password": "123456",
"confirmPassword": "123456"
```

Nesse endpoint podemos alterar a senha do usuário

`PATCH /users/id - FORMATO DA REQUISIÇÃO`

```json
"url": "123456",
```

Nesse endpoint podemos alterar a foto do usuário
