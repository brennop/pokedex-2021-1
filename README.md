# Pokedex

![](https://i.redd.it/hup9hsnlw7311.jpg)

- [Pokedex](#pokedex)
  * [Descrição do Problema](#descri--o-do-problema)
  * [Funcionalidades](#funcionalidades)
  * [Requisitos](#requisitos)
  * [API](#api)
    + [`GET /pokemons`](#-get--pokemons-)
    + [`GET /pokemons/:name`](#-get--pokemons--name-)
    + [`POST /users`](#-post--users-)
    + [`GET /users/:username`](#-get--users--username-)
    + [`POST https://pokedex20201.herokuapp.com/users/:username/starred/:pokemon`](#-post-https---pokedex20201herokuappcom-users--username-starred--pokemon-)
    + [`DELETE /users/:username/starred/:pokemon`](#-delete--users--username-starred--pokemon-)
  * [Dicas](#dicas)
  * [Exemplos](#exemplos)

## Descrição do Problema

Desenvolver uma aplicação em ReactJS para exploração de _pokemons_. O desenvolvimento do trabalho tem como objetivo colocar em prática os conceitos vistos em aula, bem como providenciar um exemplo de aplicação de escala maior para treinar ReactJS.

## Funcionalidades

- **Exploração**: o usuário deve ser capaz de visualizar uma listagem de pokemons, que serão fornecidos por uma API.
- **Informações**: o usuário deve ser capaz de visualizar as informações de um pokemon específico em uma visualização exclusiva (modal, página, etc.).
- **Autenticação**: usando a API, um usuário deve ser capaz de se autenticar na aplicação.
- **Favoritos**: um usuário autenticado deverá poder favoritar pokemons, e visualizar seus pokemons favoritados.

## Requisitos

- O projeto deverá ser desenvolvido com a ajuda do [Git](https://brennop.github.io/wiki/#/git/guia). O repositório do projeto deverá ser subido para o GitHub.
- Ao final do projeto, a aplicação deverá ser hospedada em algum serviço de hospedagem, como o [Netlify](https://www.netlify.com/).
- O projeto deverá ser executado em _dupla_.
- O link do repositório do projeto e da aplicação hospedada deverão ser entregues até dia XX/11/2020.

## API

Para executar o projeto, disponibilizamos uma API REST com algumas rotas úteis.

A API está disponível em [`https://pokedex20201.herokuapp.com`](https://pokedex20201.herokuapp.com)

---

### `GET /pokemons`

Retorna um documento JSON contendo 25 pokemons. Pode ser página usando `?page=X` no final da rota, onde X é a página desejada.

Exemplo:

```
GET https://pokedex20201.herokuapp.com/pokemons?page=2
```

```json
{
  "data": [
    {
      "id": 26,
      "name": "raichu",
      "image_url": "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/26.png",
      "number": 26,
      "weight": 300,
      "height": 8,
      "kind": "electric",
      "created_at": "2020-05-25T04:48:23.665Z",
      "updated_at": "2020-05-25T04:48:23.665Z"
    },
...
  ],
  "size": 25,
  "next_page": 3,
  "prev_page": 1
}
```

---

### `GET /pokemons/:name`

Recebe informações sobre o pokemon com nome `:name`.


Exemplo:

```
GET https://pokedex20201.herokuapp.com/pokemons/bulbasaur
```

```json
{
  "id": 1,
  "name": "bulbasaur",
  "image_url": "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/1.png",
  "number": 1,
  "weight": 69,
  "height": 7,
  "kind": "grass;poison",
  "created_at": "2020-05-25T04:48:23.225Z",
  "updated_at": "2020-05-25T04:48:23.225Z"
}
```

---

### `POST /users`

Registra um usuário com um `username`. Precisa que `username` seja enviado no corpo da requisição.

Exemplo:

```
POST https://pokedex20201.herokuapp.com/users username="ash_ketchum"
```

---

### `GET /users/:username`

Obtém informações do usuário `:username`, incluindo os seus pokemons favoritados.

Exemplo:

```
GET https://pokedex20201.herokuapp.com/users/ash_ketchum
```

```json
{
  "user": {
    "id": 1,
    "username": "ash_ketchum",
    "created_at": "2020-05-29T03:11:03.285Z",
    "updated_at": "2020-05-29T03:11:03.285Z"
  },
  "pokemons": [
    {
      "id": 12,
      "name": "butterfree",
      "image_url": "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/12.png",
      "number": 12,
      "weight": 320,
      "height": 11,
      "kind": "flying;bug",
      "created_at": "2020-05-25T04:48:23.423Z",
      "updated_at": "2020-05-25T04:48:23.423Z"
    },
   ...
  ]
}
```

---

### `POST https://pokedex20201.herokuapp.com/users/:username/starred/:pokemon`

Acrescenta o pokemon com nome `:pokemon` à lista de favoritos do usuário `:username`. Não precisa de argumentos adicionais no corpo.


```
POST https://pokedex20201.herokuapp.com/users/ash_ketchum/starred/pikachu
```

---

### `DELETE /users/:username/starred/:pokemon`

Remove o pokemon com nome `:pokemon` da lista de favoritos do usuário `:username`.

```
DELETE https://pokedex20201.herokuapp.com/users/ash_ketchum/starred/pikachu
```

---

## Dicas

- Use a biblioteca [react-router-dom](https://reactrouter.com/web/guides/quick-start) para criar rotas na sua aplicação e separar as views.

- Use a biblioteca [axios](https://github.com/axios/axios) para realizar requisições à API dentro da aplicação.

- Use a ferramenta [Insomnia](https://insomnia.rest/) para testar as requisições à API e verificar seus resultados.

- Use a biblioteca [styled-components](https://styled-components.com/) para facilitar a estilização dos componentes. _[Opicional]_

## Exemplos 

> Copiem à vontade, mas sejam criativos

- https://www.pokemon.com/br/pokedex/
- https://pokedex.org/
- https://dapedofonpokedex.netlify.app
- https://gifted-poitras-7dd2d5.netlify.app/
- https://pokedex.brn.wtf/
