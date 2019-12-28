<template>
  <Layout>
    <h1>Blog</h1>
    <article v-for="edge in $static.allPost.edges" :key="edge.node.id">
      <h2>{{ edge.node.title }}</h2>
      <p>{{ edge.node.excerpt }}</p>
      <p>Posted {{ edge.node.date }} - {{ edge.node.timeToRead }} min read</p>
      <div>
        <span
          style="padding-right: .25em"
          v-for="tag in edge.node.tags"
          :key="tag"
          >#{{ tag }}</span
        >
      </div>
    </article>
  </Layout>
</template>

<static-query>
{
  allPost {
 		edges {
      node {
        id
        title
        excerpt
        date (format: "MMMM Do, YYYY")
        tags
        timeToRead
      }
    }
  }
}
</static-query>
