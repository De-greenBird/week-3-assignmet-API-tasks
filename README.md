# Week 3 - CRUD Todo API

A simple Express.js Todo API built for the Week 3 assignment.

## Setup

```bash
npm install
node app.js
```

Server runs at `http://localhost:3002`.

## Routes

| Method | Route            | Description                              |
|--------|------------------|--------------------------------------------|
| GET    | /todos           | List all todos                            |
| GET    | /todos/active    | List todos where `completed` is false     |
| GET    | /todos/completed | List todos where `completed` is true      |
| GET    | /todos/:id       | Get a single todo by id                   |
| POST   | /todos           | Create a todo (`task` field required)     |
| PATCH  | /todos/:id       | Partial update of a todo                  |
| DELETE | /todos/:id       | Delete a todo                             |

## Example requests

**Create a todo**
```bash
curl -X POST http://localhost:3002/todos \
  -H "Content-Type: application/json" \
  -d '{"task": "Write assignment README"}'
```

**Missing task field (400 error)**
```bash
curl -X POST http://localhost:3002/todos \
  -H "Content-Type: application/json" \
  -d '{}'
```

**Get one todo**
```bash
curl http://localhost:3002/todos/1
```

**Get active (incomplete) todos**
```bash
curl http://localhost:3002/todos/active
```

## Notes

- `/todos/active` is declared before `/todos/:id` in the router so Express
  doesn't mistake "active" for an `:id` parameter.
- Data is stored in memory and resets whenever the server restarts.