# Using Graphql-Faker

## CLI

1.  Run `graphql-faker /ext-swapi.graphql --extend http://swapi.apis.guru` from root where `/ext-swapi.graphql` is the name of the file graphql-faker will create in your root dir with whatever you write in the Graphql Faker editor. on localhost:900s/editor. `--extend http://swapi.apis.guru` is the running server you want to add fake data to. To run same on local instance point extend to server endpoint running locally. If we test wtih swapi running local, the local swapi server we are pointing to would exist on http://localhost:52289/.

2.  In editor, right your extension and hit save:

```gql
type Avatar {
  #The original avatar URL
  originalUrl: String @fake(type: avatarUrl, options: { imageCategory: people })
  # The thumbnail resized to 64x64px
  thumbnail64Url: String
    @fake(type: imageUrl, options: { imageWidth: 64, randomizeImageUrl: true })
}

extend type Person {
  #The avatar of the user
  avatar: Avatar
}
```

* this will generate a file in your root repo.

- the type your extending has to exists on the schema you are extending, obviously. So if Person, which exists on swapi schema can be extended with our new avatar schema type.

3.  Visualize your changes in GraphiQl

    <img width="350" alt="screenshot 2017-09-22 10 48 08" src="./images/Screen Shot 2018-04-15 at 1.46.33 PM.png">

4.  Try your query:

<img width="350" alt="screenshot 2017-09-22 10 48 08" src="./images/Screen Shot 2018-04-15 at 1.52.48 PM.png">
