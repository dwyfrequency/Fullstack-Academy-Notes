# Fullstack-Academy-Notes

Notes from my time at fullstack academy

## 🐣 Junior Phase

### Week 1

Git, HTML & CSS, DOM & Events - Vanilla Js

#### Day 1: Collaboration

- Reading:

  - [📖 Git Basics](https://git-scm.com/book/en/v2/Getting-Started-Git-Basics)

- Notes:

* Takeaways:

#### Day 2: HTML & CSS, Debugging

- Reading:

  - [📖 HTML Basics](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/HTML_basics)
  - [📖 What is the DOM?](https://css-tricks.com/dom/)
  - [📖 CSS Basics](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/CSS_basics)
  - [📖 Calculate Specificity](https://slicejack.com/quick-guide-to-css-specificity/)
  - [📖 Calculate Specificity v2](https://css-tricks.com/specifics-on-css-specificity/)
  - [📖 REM vs EM vs PX](https://engageinteractive.co.uk/blog/em-vs-rem-vs-px) \* [📖 CSS Units Ultimate Guide](https://blog.alexdevero.com/css-units-ultimate-guide/)

- Notes:

* Takeaways:

#### Day 3: DOM and Events

- Reading:
  - Events
    - [📖 An Intruction to DOM Events](https://www.smashingmagazine.com/2013/11/an-introduction-to-dom-events/)
  - CSS
    - [CSS Grow](https://css-tricks.com/flex-grow-is-weird/)
    - [CSS Center](https://css-tricks.com/centering-css-complete-guide/)
    - [Colorful Flexbox](https://medium.freecodecamp.org/even-more-about-how-flexbox-works-explained-in-big-colorful-animated-gifs-a5a74812b053)
  - Dom Datatypes
    - [HTML Collection vs NodeList](https://teamtreehouse.com/community/understanding-the-difference-between-an-htmlcollection-and-a-nodelist)
    - [NodeList Doc](https://developer.mozilla.org/en-US/docs/Web/API/NodeList)

#### Day 4: Pixelate, Trackr

- Notes:

* Takeaways:

#### Day 5: Conway's Game of Life

- Notes:

* Takeaways:

  Struggled with the neighbor algo and the step function.

#### Weekend 1: Fitness Tracker and Pixelate

- Notes:

  I completed the checkpoint for the fitness tracker. The fitness tracker used flexbox and vanilla js. At first for the tracker, I had a giant func to calc analytics for the sidebar. Then, I broke it down into multiple tiny functions. I didnt write any tests for it. In the future, I'm going to try and do more test driven development

  Next, I tried to redo the [pixelate project](https://github.com/dwyfrequency/Reactive-Pixel-Board) in react. I created a monolith component App using hooks. I had an issue with the design of the component. Should I break it down into multiple. How do I handle the functions to paint all the cells, and paint the remaining. I found the project to be easy when down with vanilla js, but incredibly difficult with react.

  - Issues with pixelate:

    - what should i componentize?
    - do i need to employ useEffect?
    - what should i maintain in the state?
    - how should i dynamically update each cell without re-rending the whole board and losing the styling?

- Takeaways:

  I need to focus on component design, understanding the useEffect hook and its use cases, what warrants being in state.

### Week 2

Node, Express, Sequelize

#### Day 1: Intro to Node & Express

- Reading:

  - [📖 What Exactly is Node.js](https://medium.freecodecamp.org/what-exactly-is-node-js-ae36e97449f5)
  - [📖 A Simple Explanation of Express Middleware](https://medium.com/@agoiabeladeyemi/a-simple-explanation-of-express-middleware-c68ea839f498)
    - ## Middleware:

- Notes:

  - Node: lets us write javascript on the server. It uses the V8 engine to compile our js to machine code. Allows for new environments for our javascript aside from the browser.
    - when typing node keyword on our command line, it takes the js code creates a node process
    - Node modules: file/library of js code that runs specifically in the node ecosystem. Allows for separation of concerns
      - each file represents a module
      - a module has its own "global" object called "module" (similar to window in the browser, except each module has its own unique module)
      - each module has a property called "exports" (`module.exports`) using a special func called `require`
      - when importing a module in node, we use `require`. If we specify, a relative path `./` it knows it's a package we wrote. If it just has the package name, it's in our node_modules
      - module: packaging of reusable code
      - when exporting, we use `module.exports =` and assign it a value.
  - server: program that listen to requests and provides a response.
    - Why create one?
  - Program vs Process:
    - we are going to be writing programs that will be turned into node processes
  - asynchronicity:
    - async code: code that may take a variable amount of time. (code is asynchronous if) the execution order is not dependent upon the command order
    - Example Use Case: query a db.
  - concurrency types:
    - single threaded blocking
    - single threaded non-blocking
    - multithreaded
  - Event loop:
    - stack and queue
      - stack: LIFO, last item added is the first one removed. think stack of dishes, we wash the one on top
      - queue: FIFO, first item added is the first to be removed.
    - will need to provide a picture of this
  - Express:
    - wrapper over the built in http node library. Makes it even easier to write and maitain
    - express route handlers two params
      1. endpoint
      2. callback (req, res, next)
  - Http:
    - HTTP Verbs: Get, Post, Put, Delete
      - Get: retrieve data
      - Post: add new data
      - Put: update existing data
      - Delete: delete existing data
  - REST (Representational State Transfer) APIs
    - apis take a url query string and returns a response

- Takeaways:

#### Day 2: Databases & SQL

- Reading:

  - [📖 Schema Design Overview](https://medium.com/@kimtnguyen/relational-database-schema-design-overview-70e447ff66f9)
  - [📖 SQL W3schools](https://www.w3schools.com/sql/sql_intro.asp) \* [📖 What is a RDBMS anyway?](https://www.codecademy.com/articles/what-is-rdbms-sql)

- Notes:

  - RMDB: relational database management system
    - We use POSTGRES with tool postico.
      - postico lets us have a nice gui to setup tables and query the db so we dont need to use the cli
  - ## SQL (Structured Query Language) - allows us to write declarative code to access DB. Used to create/read/update/delete (crud) data
  - SQL Syntax: - JOIN: allows us to combine tables passed on a condition
    ```
    SELECT Students.ID, Name, Street, Zip, City
      FROM Students
    JOIN Addresses
      ON Students.Address = Addresses.ID
    ```
  - node module `pg` connects our node app to our postgres db server.

- Takeaways:

  - Didnt do a great job of focussing on the lectures. I dealing with a few pesky react issues that side tracked me :(

#### Day 3: Postgres & Express Routing

- Reading:

  - [async-await-slides]: 01-junior-phase/08-async-pg-express/async-await.pdf
  - [node-postgres-slides]: 01-junior-phase/08-async-pg-express/node-postgres.pdf
  - [restful-express-slides]: 01-junior-phase/08-async-pg-express/express-routes.pdf
  - [node-postgres-video]: https://youtu.be/v3VF85twzrY
  - [restful-routing-video]: https://youtu.be/_EdRU737ypE

- Notes:

  - async:

    - `async` declares our function as asynch. `async () => {}`. This will always return a promise
    - `await` is declared when receiving a value from an async func.
      - ```
        <!-- this example does not return 5 need to look into docs on what setTimeout returns -->
        const func = async () => {
          setTimeout(() => 5, 10)
        }
        const x = await func()
        ```

  - Express:
    - `express` is a web application framework that provides a robust set of features for web and mobile applications.
    - `morgan` is our logger
    - `body-parser` allows us to parse the data our client is sending either in body or url.
    - `const app = express();` instantiates our express instance;
    - `app.use`
    - `app.use(express.static(__dirname + '/public'));` says treat this public folder as our root directory.
    - `app.use(express.urlencoded({ extended: false }));` when to use this vs the json encoded version.

- Takeaways:
  - review solutions code for wizards 3. I struggled with the database interactions <br /> - specifically chaining inserts with select statements.

#### Day 4: ORM & WikiStack 1

- Reading:

- Notes:

  - ORM: Object Relational Map
    - acts as a "bridge" between your code and RDBMS
    - using ORM, data an be easily stored and retrieved from a database without writing SQL statements directly

- Takeaways:
