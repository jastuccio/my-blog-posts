# Creating a Blog with Gatsby [link](https://www.gatsbyjs.org/blog/2017-07-19-creating-a-blog-with-gatsby/)
by [Dustin Schau](dustinschau.com/blog)

Gatsby v1.0.0 gives us:
* the ability to create content queries with GraphQL
* CMS integration with
  * WordPress, Contentful, Drupal, etc.
* route based code splitting to keep the end-user experience snappy

Install the CLI
`npm install -g gatsby-cli`

create the folder personal-blog and then change into that directory `gatsby new personal-blog && cd $_`

launch the local development server
`gatsby develop`

------

## Functional plugins

* can implement functionality (e.g. offline support, generating sitemaps, etc.)
* or extend Gatsby’s webpack config by adding support for typescript, sass, etc.

`npm i --save gatsby-plugin-catch-links gatsby-plugin-react-helmet` (*`yarn add` can also be used*)

"catch-links" implements the history pushState API, and does not require a page reload on navigating to a different page in the blog

"react-helmet" is a tool that allows for modification of the head tags; Gatsby statically renders any of these head tag changes

------
edit `gatsby-config.js`

```javascript
module.exports = {
  siteMetadata: {
    title: `Your Name - Blog`,
    author: `Your Name`,
  },
  plugins: [
    'gatsby-plugin-catch-links',
    'gatsby-plugin-react-helmet',
  ],
}
```

we now have the ability to edit our site’s head tags, as well as implement a single page app feel without reloads

------

## Source plugins

create nodes which can then be transformed into a usable format (if not already usable) by a transformer plugin.

install the plugin:
$ `npm i --save gatsby-source-filesystem`

inject into our gatsby-config.js
```javascript
module.exports = {
  // previous configuration
  plugins: [
    'gatsby-plugin-catch-links',
    'gatsby-plugin-react-helmet',
    {
      resolve: `gatsby-source-filesystem`,
      options: {
        path: `${__dirname}/src/pages`,
        name: 'pages',
      },
    }
  ]
}
```
------

### Transformer plugins

take some underlying data format that is not inherently usable in its current form (e.g. Markdown, json, yaml, etc.), and transforms it into a format that Gatsby can understand, and that we can query against with GraphQL.

* gatsby-transformer-remark
  * Uses the remark Markdown parser to transform .md files on disk into HTML

`npm i --save gatsby-transformer-remark`

edit `gatsby-config.js`

```javascript
module.exports = {
  // previous setup
    plugins: [
    'gatsby-plugin-catch-links',
    'gatsby-plugin-react-helmet',
    {
      resolve: `gatsby-source-filesystem`,
      options: {
        path: `${__dirname}/src/pages`,
        name: 'pages',
      },
    },
    {
      resolve: 'gatsby-transformer-remark',
      options: {
        plugins: [] // just in case those previously mentioned remark plugins sound cool :)
      }
    },
  ]
};
```