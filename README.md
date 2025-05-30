# 🎮 API Games DSList

Este projeto é uma API RESTful desenvolvida com **Spring Boot** que fornece uma lista de jogos, permitindo consultas detalhadas ou resumidas por listas organizadas. O sistema é inspirado em um catálogo de jogos, útil para portfólios, rankings ou organização de coleções pessoais.

## 🧰 Tecnologias Utilizadas

* Java 21
* Spring Boot 3
* Spring Data JPA
* Hibernate
* Banco de Dados H2 (ambiente de desenvolvimento)
* Maven

## 📁 Estrutura do Projeto

* `entities/`: Entidades JPA que representam os objetos de domínio (`Game`, `GameList`, `BelongingPK`)
* `repositories/`: Interfaces que acessam o banco de dados via Spring Data JPA
* `services/`: Camada de serviço com regras de negócio e transações
* `dto/`: Data Transfer Objects para expor apenas os dados necessários ao cliente
* `projections/`: Interfaces para consultas customizadas no banco de dados

## 📦 Endpoints Disponíveis

| Método | Endpoint                | Descrição                                       |
| ------ | ----------------------- | ----------------------------------------------- |
| GET    | `/games`                | Lista todos os jogos (modo resumido)            |
| GET    | `/games/{id}`           | Retorna detalhes de um jogo específico          |
| GET    | `/lists`                | Lista todas as listas de jogos                  |
| GET    | `/lists/{listId}/games` | Retorna jogos vinculados a uma lista específica |

> As rotas estão disponíveis no Swagger UI se configurado ou podem ser testadas via Postman.

## 🔄 Relacionamentos

* `Game` possui relação com `GameList` através da entidade intermediária `BelongingPK` (chave composta)
* `GameList` representa categorias ou agrupamentos de jogos
* Utiliza `@Embeddable` e `@EmbeddedId` para lidar com chaves compostas

## ▶️ Como executar

1. Clone o repositório:

```bash
git clone https://github.com/jcsalerno/api-games-dslist.git
cd api-games-dslist
```

2. Compile e execute com o Spring Boot:

```bash
./mvnw spring-boot:run
```

3. Acesse a API via:

* Swagger: [http://localhost:8080/swagger-ui/index.html](http://localhost:8080/swagger-ui/index.html)
* Banco H2 Console (opcional): [http://localhost:8080/h2-console](http://localhost:8080/h2-console)

## 🗃️ Exemplo de resposta JSON

**GET `/games/1`**

```json
{
  "id": 1,
  "title": "The Witcher 3",
  "year": 2015,
  "genre": "RPG",
  "platforms": "PC, PS4, Xbox One",
  "score": 9.5,
  "imgUrl": "https://...",
  "shortDescription": "Geralt em busca de Ciri.",
  "longDescription": "Uma jornada épica em um mundo aberto com missões densas e combate profundo..."
}
```



> Projeto desenvolvido para fins didáticos e demonstração de habilidades com Spring Boot, JPA e arquitetura limpa.
