# Gatsby.js - A Modern Static Site Generator

install Gatsby using NPM

`gatsby new <sitename>` create a new site
`gatsby develop` start a server

* `gatsby-config.js` plugins and the site title, metadata
* `/public/` the generated static files
## `/src` the code you edit
  ### `/layouts`
  * `index.js`
    * imports react and other dependencies
    * `import './index.css'` loads css
    * header component
    * template wrapper
      * "helmet" sets metadata

  ### `/pages`

  -----

  general rule of thumb is if you use a component in multiple places on a site, it should be in its own module file in the components directory. But, if it’s used only in one file, create it inline.