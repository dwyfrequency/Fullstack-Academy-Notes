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

## Creating Gatsbhy Page Layout
