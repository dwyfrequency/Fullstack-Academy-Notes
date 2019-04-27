# Express Notes

## Quick Tips

## Middleware

- middleware is any function that is invoked by the Express.js before your final request handler is, and thus sits in the middle between a raw request and the final intended route.
  - `app.use(insert function here)` registers some function to run for each incoming request.

## Logging

- One of the most popular logging middlewares is morgan, created by the express team. Passing it to app.use() makes it intercept all request and responses - every time you send a response, Morgan logs the request and response information. Morgan is also very configurable, with lot's of "modes" (we recommend using the "dev" mode during development).
  - For example, after installing morgan (npm install morgan): `app.use(morgan('dev'))

## Static Routing

- We need to make sure that the express application serves up the contents of the files it finds in the /public folder. By default this folder is being completely ignored by your application - if you want express to look for files in this folder and serve them, you have to configure it to do so with `express.static`
  - Example: `app.use(express.static(path.join(\_\_dirname, 'public')));`
  - Now, everything we put in public will be automatically accessible via the URI path, as if it was actually a filepath. The browser can now make requests for public/style.css with GET /style.css.
  - After set up, all we need to do is drop a file into public somewhere, and Express will automatically route requests for it.

## Routing

- `app.get('relative endpoint', (res, req, next) => {})`

### Dynamic Routing with Parameters

- `app.get( '/posts/:id', someFunction );`
- The colon : is a trick that Express provides to define particular portions of the URI string as variables. In other words, in posts/:id, the :id portion can be anything. The variable and its value are stored on the req.params object.
