# Gatsby Notes

## Create new project

from the gatsby cli in terminal just type `gatsby new gatsby-bootcamp https://github.com/gatsbyjs/gatsby-starter-hello-world.git`

## Visiting Pages

Your endpoint will be the filename in your src dir ie. blog.js will be /blog

## Linking Between Pages

`import { Link } from "gatsby"` allows for optimization over the standard a tag.
It allows us to preload the page so it will load instantly
`<Link to="/contact">Contact me!</Link>` Same syntax as React Router
The Link component should only be used for internal pages

## Creating Shared Page components

you can create a components directory in src - the name components doesnt have any special meaning
we could name it anything. The components will only be used when they are imported into our pages.

Anytime we want to render a shared components, we should put it in this directory and import when needed

## Creating Gatsby Page Layout

Create a universal page layout - create higher order component named something like layout
have this component wrap your components that will be featured on every page like
a navbar and footer. Have your component render children ie anything nested between it

```
const Layout = props => {
  return (
    <div>
      <Header />
      {props.children}
      <Footer />
    </div>
  )
}
```

then wrap your pages with this component.

## Plugins

You can use gatsby plugins if you want to say configure it to use sass
`npm install --save node-sass gatsby-plugin-sass`
You can see all plugins on the gatsby site. After downloading, you must config gatsby.
with file name `gatsby-config.js` in your projects root director `/`

**Note** this will be a node.js file so we need to export it in module.exports

```
module.exports = {
  plugins: ["gatsby-plugin-sass"],
}
```

## Styling Your Pages
