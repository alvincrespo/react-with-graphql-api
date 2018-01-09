## React + GraphQL API

This is the API built on top of [GraphQL](http://graphql.org/) with the [Graphcool Framework](https://www.graph.cool/)

### Installation

#### [Docker](https://www.docker.com/)

Download and Install [Docker](https://docs.docker.com/docker-for-mac/install/)!

#### [NVM](https://github.com/creationix/nvm)

```
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash
```

#### [Node](https://nodejs.org/)

Install the node version specified in the repo:

```
nvm install $(cat .nvmrc)
```

#### [Graphcool CLI]

```
npm install -g graphcool
```

### Project Setup

With your dependencies installed. We'll now need to get the local
docker image up and running.

```
graphcool-framework local up
```

This may take several minutes as the image is retrieved and the environment setup.

Once thats all set, you'll need to deploy locally, and you'll need to choose
the correct options for deployment:

```
graphcool-framework deploy

? Please choose the cluster you want to deploy to

local

? Please choose the target name

dev

Creating service s-video-cool locally in cluster local... ✔
Bundling functions... 1.1s
Deploying locally... 1.0s

Success!
```

**NOTE**: There will be text after the "Success!" but I've removed that here
since it may change and be more confusing later on. The point is to note
that I've gone ahead and chosen `local` for the cluster and named the target
`dev`.

Once everything is all set, you should be able to play around with the API via:

```
graphcool-framework playground
```

This will launch a UI like:

![](https://ac-screenshots.s3.amazonaws.com/Playground_-_httplocalhost60000simplev1cjc7r0wro00040135hkyg759e_2018-01-09_16-48-46.jpg)


To make sure things run smoothly, try verifying your install with the following
queries and mutations:

```
query {
  allShows {
    id
    title
    description
    imdbId
  }
}
```

```
mutation {
  createShow(title: "Stranger Things", description: "When a young boy disappears, his mother, a police chief, and his friends must confront terrifying forces in order to get him back.") {
    id
    title
    description
  }
}
```

```
mutation {
  updateShow(id: "cjc7s8pbw00390135311o6ena", title: "Strange Things!") {
    id
    title
    description
  }
}
```

```
query {
  Show(id: PLACE_ID_OF_CREATED_SHOW_HERE) {
    id
    title
    description
  }
}

```
