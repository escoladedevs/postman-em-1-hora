# postman-em-1-hora
Materiais para o curso de Postman em 1 hora


# Simple Books API #

API para reservar um livro.

A API está disponível no endereço `https://simple-books-api.glitch.me`

## Endpoints ##

### Status ###

GET `/status`

Retorna o status da API.

### Lista de Livros ###

GET `/books`

Retorna a lista de livros.

Query parameters opcionais:

- type: fiction ou non-fiction
- limit: número entre 1 e 20


### Consulta Livro ###

GET `/books/:bookId`

Retorna informações sobre um livro em específico


### Reservar um livro ###

POST `/orders`

Reserva um livro em específico. Requer autenticação.

O request body tem que estar em formato JSON e ter as seguintes propriedades:

 - `bookId` - int - Obrigatório
 - `customerName` - String - Obrigatório

Exemplo
```
POST /orders/
Authorization: Bearer <TOKEN>

{
  "bookId": 1,
  "customerName": "Gil do Vigor"
}
```

A resposta conterá o token de acesso

### Retorna todas as reservas ###

GET `/orders`

Permite visualizar todas as reservas. Requer autenticação.

### Retorna reserva ###

GET `/orders/:orderId`

Permite visualizar uma reserva em específico. Requer autenticação.

### Atualiza reserva ###

PATCH `/orders/:orderId`

Atualiza uma ordem em específico. Requer autenticação.

O request body tem que estar em formato JSON e ter as seguintes propriedades:

 - `customerName` - String

 Exemplo
```
PATCH /orders/PF6MflPDcuhWobZcgmJy5
Authorization: Bearer <YOUR TOKEN>

{
  "customerName": "Gil do Vigor"
}
```

### Exclui reserva ###

DELETE `/orders/:orderId`

Exclui uma reserva. Requer autenticação.

A requisição deve estar vazia.

 Example
```
DELETE /orders/PF6MflPDcuhWobZcgmJy5
Authorization: Bearer <YOUR TOKEN>
```

## Autenticação ##

Para lidar com reservas, você precisará criar uma token de acesso.

POST `/api-clients/`

O request body tem que estar em formato JSON e ter as seguintes propriedades:

 - `clientName` - String
 - `clientEmail` - String

 Example

 ```
 {
    "clientName": "Gil do Vigor",
    "clientEmail": "gil@dovigor.com"
}
 ```

A resposta conterá o token de acesso.
