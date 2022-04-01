# Manabie Togo

Manabie Togo code challenge

## Features

- Using DDD Pattern as:
  - Application layer: `transport`
  - Domain layer: `domain`, `services`, `usecase`
  - Infrastructure layer: `provider`, `repository`
- Unit tests for domain functionalities.
- Unit tests for repository functionalities.
- Integration tests for auth and task APIs.

# Instructions

Make sure you have Go installed ([download](https://go.dev/dl/)). Version `1.17` or higher is required.

Make sure you have Docker installed ([instructions](https://docs.docker.com/engine/install/)).

Make sure you have `make` installed for running the scripts.

For Linux:

```sh
sudo apt install make
```

For MacOS:

```sh
brew install make
```

<br/>

## Start Server

Using command bellow to build and run on Docker Compose

```sh
make start
```

- `Togo` app will available on `127.0.0.1:4000`
- `Redis` will available on `127.0.0.1:6379`
- `PostgreSQL` will available on `127.0.0.1:55432`

To stop the server

```sh
make stop
```

<br/>

## Run Unit Tests

Using command bellow to run unit tests

```sh
make run-unit-test
```

<br/>

## Run Integration Tests

Make sure Togo server build and start successfully then use the command bellow to run integration tests.

```sh
make run-integration-test
```

<br/>

# cURL samples

Sign up:

```sh
curl --location --request POST 'http://127.0.0.1:4000/auth/register' \
--header 'Content-Type: application/json' \
--data-raw '{
    "fullName": "Foo Name",
    "username": "user_name",
    "password": "a123456",
    "tasksPerDay": 10
}'
```

Login:

```sh
curl --location --request POST 'http://127.0.0.1:4000/auth/login' \
--header 'Content-Type: application/json' \
--data-raw '{
    "username": "user_name",
    "password": "a123456"
}'
```

Get user Me:

```sh
curl --location --request GET 'http://127.0.0.1:4000/users/me' \
--header 'Authorization: Bearer <token>'
```

Update user Me:

```sh
curl --location --request PATCH 'http://127.0.0.1:4000/users/me' \
--header 'Authorization: Bearer <token>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "tasksPerDay": 1000
}'
```

Add tasks:

```sh
curl --location --request POST 'http://127.0.0.1:4000/tasks' \
--header 'Authorization: Bearer <token>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "content": "This is a task"
}'
```

Get tasks:

```sh
curl --location --request GET 'http://127.0.0.1:4000/tasks' \
--header 'Authorization: Bearer <token>'
```

Update a task:

```sh
curl --location --request PATCH 'http://127.0.0.1:4000/tasks/1' \
--header 'Authorization: Bearer <token>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "content": "text updated"
}'
```

# License

MIT
