## Postgres Notes

## DMBS

- The Database Management System is the brain of our persistent storage solution. It is responsible for translating declarative incoming queries into actual file system operations.
- For PostgreSQL, the DBMS is the postgres process running behind the scenes. In fact, postgres is a TCP/IP server listening on a port! …Not an HTTP-protocol server, but rather a Postgres-protocol server.
- DBMS Clients:
  - While the postgres DBMS/sits in the background ready to receive queries, a client can connect to it and send SQL conforming to the protocol postgres expects.
  - To connect to our db from node, we'll use a database driver. It bridges the gap between applications and DBMS through an API. We use npm package pg
  - SENDING THE DATABASE REQUEST
    1.  Node app: our code calls a function provided by pg, passing a string SQL query
    2.  pg driver: connects to postgres as a client and sends the SQL query using correct protocol
    3.  postgres server: translates query into executing a series of file system operations
  - RECEIVING THE DATABASE RESPONSE
    1.  postgres server: sends result of file system ops back to connected pg driver
    2.  pg driver: parses the raw response and builds a JS array of row data
    3.  Node app: receives a Promise that will eventually contain the array.

## `psql` client: a human interface(shell)

- The psql shell is a client designed to accept SQL queries input via keyboard, transmit those queries to postgres, and print the results. It is conceptually similar to the Bash prompt. Internally, psql knows how to form a connection to & communicate with postgres.

## Syntax Notes

- For our queries, we can use string interpolation for dynamic values. `select * from posts where id = $1`,
  [req.params.id]`
  - you can include numbers appended with the $ symbol in your querystring, and include an array of arguments to pass to the query (note: index 0 of the array corresponds to $1 in the query):
