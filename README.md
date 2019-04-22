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
  _ [📖 HTML Basics](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/HTML_basics)
  _ [📖 What is the DOM?](https://css-tricks.com/dom/)
  _ [📖 CSS Basics](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/CSS_basics)
  _ [📖 Calculate Specificity](https://slicejack.com/quick-guide-to-css-specificity/)
  _ [📖 Calculate Specificity v2](https://css-tricks.com/specifics-on-css-specificity/)
  _ [📖 REM vs EM vs PX](https://engageinteractive.co.uk/blog/em-vs-rem-vs-px) \* [📖 CSS Units Ultimate Guide](https://blog.alexdevero.com/css-units-ultimate-guide/)

- Notes:

* Takeaways:

#### Day 3: DOM and Events

- Reading:
  - Events
    - [📖 An Intruction to DOM Events](https://www.smashingmagazine.com/2013/11/an-introduction-to-dom-events/)
  - CSS
    _ [CSS Grow](https://css-tricks.com/flex-grow-is-weird/)
    _ [CSS Center](https://css-tricks.com/centering-css-complete-guide/)
    - [Colorful Flexbox](https://medium.freecodecamp.org/even-more-about-how-flexbox-works-explained-in-big-colorful-animated-gifs-a5a74812b053)
  - Dom Datatypes
    _ [HTML Collection vs NodeList](https://teamtreehouse.com/community/understanding-the-difference-between-an-htmlcollection-and-a-nodelist)
    _ [NodeList Doc](https://developer.mozilla.org/en-US/docs/Web/API/NodeList)

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
    - Node:
      - lets us write javascript on the server. It uses the V8 engine to compile our js to machine code.
  - [📖 A Simple Explanation of Express Middleware](https://medium.com/@agoiabeladeyemi/a-simple-explanation-of-express-middleware-c68ea839f498)
    - ## Middleware:

- Notes:

  - async code: code that may take a variable amount of time.
    - Example Use Case: query a db.

- Takeaways:
