# Using the GraphQL playground

When the Gatsby development server is running, it will include GraphiQL, which is a browser-based tool you can use to query/inspect the GraphQL database associated with your site.

You can access the GraphiQL interface at: [http://localhost:8000/\_\_\_graphql](http://localhost:8000/___graphql)

## How to Query

You can query nodes created from Drupal like the following:

```javascript
{
  allArticle {
    edges {
      node {
        title
        internalId
        created(formatString: "DD-MMM-YYYY")
      }
    }
  }
}
```

With GraphiQL you can run queries to see the data from the Drupal site that Gatsby pulled in. When exploring the data in GraphiQL you’ll see that Gatsby groups Drupal content into collections based off of the content type \(“allNodeMovie”, “allNodeLandingPage”, etc.\)

Here’s a query you can run to get the title, body, and some other fields for all of the movie content type nodes in Drupal:

```graphql
query MyQuery {
  allNodeMovie {
    edges {
      node {
        body {
          processed
        }
        title
        field_mpaa_rating
        field_promo_sentence
        relationships {
          field_genres {
            name
          }
        }
      }
    }
  }
}
```

Note that if your Drupal content type has entity reference fields \(such as a reference to media or a taxonomy term\), these will be included in GraphQL under “relationships”.

{% hint style="info" %}
**Further reading:** [How To GraphQL](https://www.howtographql.com/)
{% endhint %}

