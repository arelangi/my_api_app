# Ruby Articles API

This is a Ruby on Rails application providing a RESTful API for creating, updating, and deleting articles. It uses standard REST conventions to allow API consumers to interact with article resources.

## Getting Started

To get the application running on your local machine, follow these instructions.

### Prerequisites

- Ruby (Check `.ruby-version` for the specific version)
- Rails
- SQLite3 (or the database of your choice, configured in `config/database.yml`)

### Installation

Clone the repository:

```
git clone <REPOSITORY_URL>
cd <REPO_NAME>
```

Install the required gems:

```
bundle install
```

Create and migrate the database:

```
rails db:create
rails db:migrate
```

Start the Rails server:

```
rails server
```

Now, the API should be available at [http://localhost:3000/](http://localhost:3000/)


### API Endpoints

The following API endpoints are available:

#### Articles
- GET /articles - Returns a list of all articles.
- GET /articles/:id - Returns a single article specified by the :id parameter.
- POST /articles - Creates a new article with the provided title and body.
- PATCH/PUT /articles/:id - Updates the article specified by the :id parameter with the provided title and body.
- DELETE /articles/:id - Deletes the article specified by the :id parameter.

#### Request & Response Examples

##### GET(Index) /articles

Request: `curl -X GET http://localhost:3000/articles`

Response body (JSON):

```
[
  {
    "id": 1,
    "title": "First Article",
    "body": "This is the body of the first article",
    "created_at": "2024-01-22T20:14:26.782Z",
    "updated_at": "2024-01-22T20:14:50.054Z"
  },
  {
    "id": 2,
    "title": "Second Article",
    "body": "This is the body of the second article"
    "created_at": "2024-01-22T20:14:26.782Z",
    "updated_at": "2024-01-22T20:14:50.054Z"
  }
]
```

##### GET(Show) /articles/:id

Request: `curl -X GET http://localhost:3000/articles/1`

Response body (JSON):

```
{
    "id": 1,
    "title": "First Article",
    "body": "This is the body of the first article",
    "created_at": "2024-01-22T20:14:26.782Z",
    "updated_at": "2024-01-22T20:14:50.054Z"
}
```


##### POST(Create) /articles

Request: `curl -X POST http://localhost:3000/articles -H "Content-Type: application/json" -d '{"title": "New Article", "body": "Article body"}'
`


Response body (JSON):

```
{
  "id": 3,
  "title": "New Article",
  "body": "Article body",
  "created_at": "2024-01-24T05:35:38.097Z",
  "updated_at": "2024-01-24T05:35:38.097Z"
}
```

##### POST(Create) /articles/:id

Request: `curl -X PUT http://localhost:3000/articles/1 -H "Content-Type: application/json" -d '{"title": "Updated Title", "body": "Updated body"}'
`

Response body (JSON):

```
{
  "title": "Updated Title",
  "body": "Updated body",
  "id": 1,
  "created_at": "2024-01-22T20:14:26.782Z",
  "updated_at": "2024-01-22T20:14:50.054Z"
}
```

##### DELETE(Destroy) /articles/:id

Request: `curl -X DELETE http://localhost:3000/articles/1`

Response body (JSON): None