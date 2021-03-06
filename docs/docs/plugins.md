---
title: Plugins
---

Plugins are Node.js packages that implement Gatsby APIs. They enable you to
easily solve common website build problems e.g. setup Sass, add markdown
support, process images, etc.

For larger / complex sites, they let you modularize your site customizations
into site-specific plugins.

Gatsby has a large and growing set of plugins. To search/browse official and
community plugins and their documentation, visit the [Plugin Library](/packages/).

For documentation on the different types of plugins and the functionality provided by each, see the [Plugin Authoring page](/docs/plugin-authoring/).

For a walkthrough of how to build and publish your own plugin, see the [Source Plugin Tutorial](/docs/source-plugin-tutorial/)

## How to use Gatsby plugins?

Gatsby plugins are Node.js packages, so you can install them like other packages in
node using NPM.

For example, `gatsby-transformer-json` is a package which adds support for JSON
files to the Gatsby data layer.

To install it, in the root of your site you run:

`npm install --save gatsby-transformer-json`

Then in your site's `gatsby-config.js` you add `gatsby-transformer-json`
to the plugins array like:

```javascript
module.exports = {
  plugins: [`gatsby-transformer-json`],
}
```

Plugins can take options. Examples:

```javascript
module.exports = {
  plugins: [
    // Shortcut for adding plugins without options.
    "gatsby-plugin-react-helmet",
    {
      // Standard plugin with options example
      resolve: `gatsby-source-filesystem`,
      options: {
        path: `${__dirname}/src/data/`,
        name: "data",
      },
    },
    {
      resolve: "gatsby-plugin-offline",
      // Blank options, equivalent to string-only plugin
      options: {
        plugins: [],
      },
    },
    {
      resolve: `gatsby-transformer-remark`,
      options: {
        // plugins inside plugins
        plugins: [`gatsby-remark-smartypants`],
      },
    },
  ],
}
```

Note that plugin options will be stringified by Gatsby, so they cannot be functions.
