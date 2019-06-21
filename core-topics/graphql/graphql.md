# Graphql Notes

```
query {
  allTodos(_size: 5) {
    data {
      _id
      title
      completed
    }
  }
}

```

```
# Write your query or mutation here
mutation {
  createTodo(data: {
    title: "testin123"
    completed: false
  }){
    title
    completed
  }
}
```
