# Configure Gatsby for Drupal

Before we can query Drupal's content with GraphQL, we need to perform some configuration in Drupal and Gatsby.

## Drupal

* Enable Drupal Core's module [JSONAPI](https://www.drupal.org/project/jsonapi).  This step has already been done in our Drupal instance in Pantheon.

## Gatsby

* Install and configure [gatsby-source-drupal](https://www.gatsbyjs.com/plugins/gatsby-source-drupal/) plugin by running

```bash
npm install gatsby-source-drupal
```

* Open `gatsby-config.js` in your code editor and add the following code

```js
module.exports = {
  plugins: [
    {
      resolve: `gatsby-source-drupal`,
      options: {
        baseUrl: `https://dev-nitflexapp.pantheonsite.io/`,
        apiBase: `jsonapi`, // optional, defaults to `jsonapi`
      },
    },
  ],
}
```

* Stop (`Ctrl + C`), and restart (`npm run start`) Gatsby

### Test Drupal connection

* Launch GraphQL's playground, [http://localhost:8000/___graphql](http://localhost:8000/___graphql)

* The middle column of the playground should show a query for `allNodeMovie`.  Click the Play button to run the query.

* Once the query completes, you should see the results of the query on the far right column.  This is a confirmation that your drupal configuration is correct.
