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

create a `/styles` directory to store your css files

## Using Css Modules with Gatsby

css modules are included by default

```
import headerStyles from "./header.module.scss"
...
<Link to="/" className={headerStyles.link}>Main</Link>
```

`.link` corresponds to the className in our file
`.nav-link` in our css will resolve to `navLink` in our js ie. `headerStyles.navLink`

## Graphql with Gatsby

Access with [link](http://localhost:8000/___graphql)

If we add the below to our gatsby config
`siteMetadata` for when you want to reuse common pieces of data across the site (for example, your site title), you can store that data in siteMetadata:

gatsby-config.js

```
module.exports = {
  siteMetadata: {
    title: `Gatsby`,
    siteUrl: `https://www.gatsbyjs.org`,
    description: `Blazing fast modern site generator for React`,
  },
}
```

In graphiql editor, we can click through the docs on the right hand side. Docs > query > site > Site > siteMetadata. If you do not see the siteMetadata in the docs, restart the server

sample query to grab our title

```
query {
  site {
    siteMetadata {
      title
    }
  }
}
```

```
import {graphql, useStaticQuery } from "gatsby"
const data = useStaticQuery(graphql`
    query {
      site {
        siteMetadata {
          title
        }
      }
    }
  `)

  <Link to="/" className={headerStyles.title}>
    {data.site.siteMetadata.title}
  </Link>
```

now we can access this dynamic data stored in our gatsby config

to swap IDE for graphql - we can create an env variable
file in root proj directory `.env.development` with content
`GATSBY_GRAPHQL_IDE=playground`

stop server and run command `npm install --save-dev env-cmd`

package.json
`"develop": "env-cmd -f .env.development gatsby develop",`

## Sourcing Content From Filesystem

use pluggin `gatsby-source-filesystem`
to transform markdown files in addition use pluggin `gatsby-transformer-remark`

```
{
      resolve: "gatsby-source-filesystem",
      options: {
        name: "src",
        path: `${__dirname}/src/`,
      },
    },
        "gatsby-transformer-remark",

```

## Generate Slugs for Posts

`gatsby-node.js` creating this file in your root proj folder. We can access gatsby's node APIs
