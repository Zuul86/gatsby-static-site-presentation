# Gatsby

<img alt="Gatsby" src="https://www.gatsbyjs.org/monogram.svg" width="300">

### A static site generator built on React!
---

## Adam Pritzl

![Adam](assets/Adam_Pritzl.png)

* 15+ years developer XP
* C# / .NET / JavaScript, React, Angular...
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

## HTML

```html
<html>
  <head>
  </head>
  <body>
  </body>
</html>
```
@[1-3, 6]

---

## Layout

```html
<html>
  <head>
  </head>
  <body>
    <header>
      <Menu />
    </header>
    <!--Content-->
    <footer>
      <!--footer content -->  
    </footer>
  </body>
</html>
```
@[5-7, 9-11]

---

## Page Component

```javascript
class About extends ReactComponent {
  render(){
    return (
      <div>
        <!--About page content goes in here -->
      </div>
    );
  }
}
```

---

## Page Template Setup - gatsny-node.js

```javascript
exports.createPages = ({ graphql, boundActionCreators }) => {
  const { createPage } = boundActionCreators;

  return new Promise((resolve, reject) => {
    const blogPost = path.resolve("./src/templates/blog-post.jsx");
    resolve(
      graphql(
      `
      {
        allMarkdownRemark(limit: 1000) {
          edges {
            node {
              frontmatter {
                path
              }
            }
          }
        }
      }
      `).then(result => {
        if (result.errors) {
          console.log(result.errors);
          reject(result.errors);
        }

        // Create blog posts pages.
        _.each(result.data.allMarkdownRemark.edges, edge => {
          createPage({
            path: edge.node.frontmatter.path,
            component: blogPost,
            context: {
              path: edge.node.frontmatter.path,
            },
          });
        });
      })
    );
  });
};
```

---
## Page Template Component

```javascript
class BlogPostTemplate extends React.Component {
  render() {
    const {markdownRemark: post} = this.props.data;
    const siteTitle = get(this.props, 'data.site.siteMetadata.title');

    return (
      <div className="blog-page">
        <Helmet title={`${post.frontmatter.title} | ${siteTitle}`} />
        <h1>
          {post.frontmatter.title}
        </h1>
        <p className="blog-date">
          {post.frontmatter.date}
        </p>
        <div dangerouslySetInnerHTML={{ __html: post.html }} />
        <hr />
      </div>
    );
  }
}

export default BlogPostTemplate;

export const pageQuery = graphql`
  query BlogPostByPath($path: String!) {
    site {
      siteMetadata {
        title
        author
      }
    }
    markdownRemark(frontmatter: { path: { eq: $path } }) {
      id
      html
      frontmatter {
        title
        date(formatString: "MMMM DD, YYYY")
      }
    }
  }
`;
```

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
        trackingId: `UA-00000000-1`,
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

- Continuous Delivery
- Free SSL
- Global CDN
- Cached Dependencies for _Fast_ builds

---
## Thank you!

##### Adam Pritzl

||| 
|-------------| -------------|
|@fa[twitter-square] Zuul86|@fa[link] https://www.adampritzl.com|
|@fa[linkedin-square] apritzl|@fa[link] **Slides** https://goo.gl/WKGoub|
|@fa[github-square] Zuul86|@fa[envelope-square] zuul86@gmail.com| 