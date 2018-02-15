# Gatsby

<img alt="Gatsby" src="https://www.gatsbyjs.org/monogram.svg" width="300">

### A static site generator built on React!
---

## Adam Pritzl

![Adam](assets/Adam_Pritzl.png)

* 15+ years developer XP
* C# / .NET / Javascript, React, Angular...
* Consultant with Centare
* Love learning and sharing

---

# Static site?

Note: What is it?  Why would you use it?

---

## Getting Started

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

### _Probably not_

---

## Plugins FTW!

- Sourcing Data
- Transforming Data
- Creating pages, sitemaps, RSS feeds...
- Writing things into the HTML like meta tags, js snippets
- Modifying webpack config

---

## Plugin Examples

- **gatsby-source-filesystem**
- **gatsby-source-wordpress**
- **gatsby-transformer-remark** 
- **gatsby-transformer-json** 
- **gatsby-plugin-feed**
- **gatsby-plugin-typescript**

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

# How do we get data?

---

## GraphQL

<img src="http://graphql.org/img/logo.svg" width="300" />

Note: Works similar to SQL.  Describe the data you want. Page and Layout components get the data. Demo.

---
## GraphQL
### Demo

```shell
http://localhost:8000/___graphql
```

---

## Deployment & Hosting

- Amazon S3
- GitHub Pages
- Netlify
- Surge.sh

---

<img src="assets/full-logo-dark.png" alt="Netlify" width="400" />

- Continueous Delivery
- Free SSL
- Global CDN
- Cached Dependencies for _Fast_ builds

---
## Thank you!

##### Adam Pritzl

||| 
|-------------| -------------|
|@fa[twitter-square] Zuul86|@fa[link] https://www.adampritzl.com|
|@fa[linkedin-square] apritzl|@fa[link] Slides http://goog.gl/stuff|
|@fa[github-square] Zuul86|@fa[envelope-square] zuul86@gmail.com| 