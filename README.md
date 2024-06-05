# Axum-Postgres CRUD App

It is a basic CRUD (Create, Read, Update, Delete) application built with the Rust and PostgreSQL Axum web framework. This project provides a simple API to manage tasks, demonstrating the integration of Axum with a PostgreSQL database.

## Prerequisites

Make sure you have the following installed on your system:

- Rust (https://www.rust-lang.org/tools/install)
- PostgreSQL (https://www.postgresql.org/download/)

## Setup

1. Clone the repository:

```bash
git clone https://github.com/MauricioRaulFerreyra/structure_basic_rust.git
cd structure_basic_rust

```

2. Build binaries
   
```bash
cargo build
```

3. Database Configuration

Create a PostgreSQL database and user by executing the following SQL commands in your PostgreSQL shell or client:

```sql
-- create user
CREATE ROLE axum_postgres WITH LOGIN PASSWORD 'axum_postgres';

-- create database
CREATE DATABASE axum_postgres WITH OWNER = axum_postgres ;

-- in your axum_postgres database
-- create task table
CREATE TABLE tasks (
  tasks_id SERIAL PRIMARY KEY,
  name VARCHAR NOT NULL,
  priority INT
);

```

Create a `.env` file in the project root and configure the `DATABASE_URL` and `SERVER_ADDRESS`:

```env
DATABASE_URL=postgres://axum_postgres:axum_postgres@127.0.0.1:5432/axum_postgres
SERVER_ADDRESS=127.0.0.1:8080

```

4. Run the application

```bash
cargo run
```

## API Endpoints

### Get all tasks

```http
GET /tasks
```
### Get by id tasks 
```http
GET /tasks/{tasks_id}
```
### Create tasks
```http
POST /tasks
Content-Type: application/json

{
  "name": "Task Name",
  "priority": 1
}

```


### Update tasks
```http
PATCH /tasks/{tasks_id}
Content-Type: application/json

{
  "name": "New Task Name",
  "priority": 2
}

```

### Delete tasks
```http
DELETE /tasks/{tasks_id}
```