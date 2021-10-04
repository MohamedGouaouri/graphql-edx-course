## Why GraphQL


## Basic queries
Let's suppose we have in our database two models
the first one Person and the second is Post.

```
  type Person{
    name: String!
    age: Int!
    posts: [Post!]!
  }

  type Post{
    title: String!
    content: String!
  }
```

\\

If a user wants to retrieve data or some fields of 
the person model it could query the server using:
```
  allPersons {
    name
  }
```
What does that mean is that the client wants all persons
but just their names.\\

If the client want to get more info about the Persons, it
could perform this query
```
  allPersons{
    name
    age
    posts {
      title
    }
  }
```

The client can limit the amount of data sent by the server
by adding arguments to the root query

```
  allPersons (last: 3) {
    name
  }
```
which returns the last two persons in the database


## Altering data (aka mutation)
If we want to mutate the data on the server we must 
send the following query
```
  mutation{
    createPerson (name: "mohamed", age: 21) {
      name
      age
    }
  }
```

## Subscription
One of the powerfull features of GraphQL is the notion
of subscription which simply means that the client and
the can open a steady connection so whenever data changes
hapen in the backend the client will be notified, this
type of API architecture is called event-driven architecture

```
  subscription {
    newPerson {
      name
      age
    }
  }
```

## Defining a schema

