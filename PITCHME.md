<h1>Gatsby</h1>
<img src="assets/gatsby.png" style="background-color: white; width: 25%; border-style: none;" />
<h3>A static site generator built on React!</h3>
---

# Adam Pritzl

![Adam](assets/Adam_Pritzl.png?classes=left)

* Consultant With Centare
* 15+ years developer XP
* C# / .NET / Javascript, React, Angular...
* Love learning and sharing

---

# Static site?

Note: What is it?  Why would you use it?

---

# Getting Started

```shell
npm install --global gatsby-cli

gatsby new blog https://github.com/gatsbyjs/gatsby-starter-blog
```

Note: basic default, gatsby-material-starter, gatsby-typescript-starter, gatsby-starter-bootstrap, gatsby-wordpress-starter

---

# This is React
# We use components here!

---

## Gatsby Components

* HTML
* Layout
* Page template
* Page

Note: Html - html, head, body tags. <br /> 
Layout - main parts of site menu, header, footer.<br /> Page template - used for programmatically building pages. <br /> Page - just like how it sounds, these components get compiled into pages

---

## Do I need Webpack?

### Probably not

---

## Plugins FTW!

- Sourcing Data
- Transforming Data
- Creating pages, sitemaps, RSS feeds...
- Writing things into the HTML like meta tags, js snippets
- Modifying webpack config

---

### Plugins installed with NPM 
### Setup in gatsby-config.js

```javascript
module.exports = {
  siteMetadata: {
    title: "Adam Pritzl - Software Developer/Consultant",
    author: "Adam Pritzl",
    email: "zuul86@gmail.com"
  },
  plugins: [
    {
      resolve: `gatsby-source-filesystem`,
      options: {
        path: `${__dirname}/src/pages`,
        name: "pages",
      },
    },
    {
      resolve: `gatsby-transformer-remark`,
      options: {
        plugins: [
          {
            resolve: `gatsby-remark-images`,
            options: {
              maxWidth: 590,
            },
          },
          {
            resolve: `gatsby-remark-responsive-iframe`,
            options: {
              wrapperStyle: `margin-bottom: 1.0725rem`,
            },
          },
          "gatsby-remark-prismjs",
          "gatsby-remark-copy-linked-files"
        ],
      },
    },
    {
      resolve: `gatsby-plugin-google-analytics`,
      options: {
        trackingId: `UA-108122421-1`,
      },
    },
    `gatsby-plugin-offline`,
    `gatsby-plugin-react-helmet`,
  ],
};

```
---

## Plugin Examples

- **gatsby-source-filesystem** - Creates File nodes from the file system
- **gatsby-source-wordpress** - Used to pull data from WordPress into Gatsby
- **gatsby-transformer-remark** - Parses markdown files
- **gatsby-transformer-json** - Parses JSON strings into objects
- **gatsby-plugin-feed** - Used to create an RSS feed
- **gatsby-plugin-typescript** - Typescript and TSX report

---

# How do we get data?

---

## GraphQL

<img src="http://graphql.org/img/logo.svg" width="50%" style="border-style: none;" />

Note: Works similar to SQL.  Describe the data you want. Page and Layout components get the data. Demo.

---

## Deployment & Hosting

---
The End
--