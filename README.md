# mini-block

Just a very simple Blog.

## Used Stack

### Building

- Docker

### Frontend

- Next

### Backend

- MongoDB
- Go CRUD

## Data

- Posts
  - \_id
  - title
  - text
  - createdAt
  - updatedAt

## Usage

Very simple:

> git clone https://github.com/Schattenbrot/mini-blog.git

Navigate to the rootfolder:

> cd mini-blog

Start docker-compose:

> docker-compose up

To stop the program (Beware: this will also delete the database-entries):

> docker-compose down

## Backend API

Simple CRUD implementation.

### Quick Overview of supported Requests

| Request           | Description                        |
| ----------------- | ---------------------------------- |
| [GET](#get)       | returns all posts or a single post |
| [POST](#post)     | posts a single post                |
| [DELETE](#delete) | deletes a post based on its id     |

### Routing

#### GET

> GET /v1/posts[/options]

| Parameter | Description                                 |
| --------- | ------------------------------------------- |
| `/`       | Returns `all posts`.                        |
| `/:id`    | Returns a `single post` based on it's `id`. |

Example for getting a single post:

```
{
  "post": {
    "_id": "6164d1faf656734a7edd868c",
    "title": "uwu",
    "text": "uwu text",
    "created_at": "2021-10-12T00:08:26.983Z",
    "updated_at": "2021-10-12T00:08:26.983Z"
  }
}
```

Example for getting all posts:

```
{
  "posts": [
    {
      "_id": "6164884b7b4bdf0578f75a8d",
      "title": "first post",
      "text": "first posts text"
    },
    {
      "_id": "6164bc53511d7d0fac32d883",
      "title": "third post",
      "text": "third post text"
    }
  ]
}
```

#### POST

> POST /v1/posts

Inserts a `post` into the database.

Example for the required body/payload:

```
{
  title: "some title",
  text: "some text",
}
```

The ID, updatedAt and createdAt fields will be automatically generated by the API.

The response of this method:

```
{
  "response": {
    "ok": true,
    "_id": "6164d4e4f656734a7edd868d"
  }
}
```

#### DELETE

> DELETE /v1/posts/:id

Deletes a post based on it's `id`.

Returns the number of deleted posts:

```
{
  "deletedCount": 1
}
```

### Models

#### Posts

    ID        string
    Title     string
    Text      string
    CreatedAt *time.Time
    UpdatedAt *time.Time

## Todo

### Building

- Add database volume to make it persistent. (Fix readme accordingly)

### Backend

- Payload validation and errors accordingly.
- Enable paging for getAllPosts (the database is bound to get bigger normally)
- Add meaningful comments.

### Frontend

- The frontend is kinda missing. So needs to be implemented at some point. Will be created in the folder "frontend".
