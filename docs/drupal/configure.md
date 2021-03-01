# Configure Gatsby for Drupal

Before we can query Drupal's content with GraphQL, we need to perform some configuration in Drupal and Gatsby.

## Drupal

* Enable Drupal Core's module [JSONAPI](https://www.drupal.org/project/jsonapi).  This step has already been done in our Drupal instance in Pantheon.

## Gatsby

* Configure Gatsby's [gatsby-source-drupal](https://www.gatsbyjs.com/plugins/gatsby-source-drupal/) plugins.

## Exercise

* Install the gatsby-source-drupal plugin by running

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
        baseUrl: `https://live-contentacms.pantheonsite.io/`,
        apiBase: `jsonapi`, // optional, defaults to `jsonapi`
      },
    },
  ],
}
```

* Stop (`Ctrl + C`), and restart (`npm run start`) Gatsby
