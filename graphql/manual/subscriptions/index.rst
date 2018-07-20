Subscriptions
=============

``subscriptions`` are essentially ``queries`` where the client receives an event whenever the value of any field changes upstream. Hasura GraphQL engine supports subscriptions for all kind of queries.

You can turn any query into a subscription by simply replacing ``query`` with ``subscription``. Try it out in the GraphiQL interface below. Try it out.

.. graphiql::
  :query:
    subscription {
      author {
        id
        name
        articles(
          where: {is_published: {_eq: true}},
          order_by: ["-published_on"],
          limit: 2
        ) {
          id
          title
          is_published
          published_on
        }
      }
    }
  :response:
    {
      "data": {
        "author": [
          {
            "id": 1,
            "name": "Justin",
            "articles": [
              {
                "is_published": true,
                "id": 16,
                "title": "sem duis aliquam",
                "published_on": "2018-02-14"
              },
              {
                "is_published": true,
                "id": 15,
                "title": "vel dapibus at",
                "published_on": "2018-01-02"
              }
            ]
          },
          {
            "id": 2,
            "name": "Beltran",
            "articles": [
              {
                "is_published": true,
                "id": 2,
                "title": "a nibh",
                "published_on": "2018-06-10"
              },
              {
                "is_published": true,
                "id": 9,
                "title": "sit amet",
                "published_on": "2017-05-16"
              }
            ]
          },
          {
            "id": 3,
            "name": "Sidney",
            "articles": [
              {
                "is_published": true,
                "id": 6,
                "title": "sapien ut",
                "published_on": "2018-01-08"
              },
              {
                "is_published": true,
                "id": 11,
                "title": "turpis eget",
                "published_on": "2017-04-14"
              }
            ]
          },
          {
            "id": 4,
            "name": "Anjela",
            "articles": [
              {
                "is_published": true,
                "id": 1,
                "title": "sit amet",
                "published_on": "2017-08-09"
              },
              {
                "is_published": true,
                "id": 3,
                "title": "amet justo morbi",
                "published_on": "2017-05-26"
              }
            ]
          }
        ]
      }
    }

All the concepts of :doc:`queries <../queries/index>` hold true with subscriptions.

Check out:

* :doc:`Simple Object Queries <../queries/simple-object-queries>`
* :doc:`Nested Object Queries <../queries/nested-object-queries>`
* :doc:`Query filters or search queries <../queries/query-filters>`
* :doc:`Sort Query Results <../queries/sorting>`
* :doc:`Paginate Query Results <../queries/pagination>`
* :doc:`Using Multiple Arguments <../queries/multiple-arguments>`
* :doc:`Multiple Queries in a Request <../queries/multiple-queries>`
* :doc:`Aggregations in Queries <../queries/aggregations>`
* :doc:`Control access to certain data<../queries/control-access>`
