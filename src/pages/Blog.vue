<template>
  <Layout>
    <h1>Blog</h1>
    <article
      v-for="edge in $static.allPost.edges"
      :key="edge.node.id"
      style="margin-bottom: 2em"
    >
      <g-image :src="edge.node.cover_image" style="width: 100%"></g-image>
      <h2>
        <g-link :to="edge.node.path">{{ edge.node.title }}</g-link>
      </h2>
      <p>{{ edge.node.excerpt }}</p>
      <p>Posted {{ edge.node.date }} · {{ edge.node.timeToRead }} min read</p>
      <div>
        <span
          style="padding-right: .25em"
          v-for="tag in edge.node.tags"
          :key="tag"
          >#{{ tag }}</span
        >
      </div>
      <!-- <g-link :to="edge.node.path">Read Post</g-link> -->
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
        path
        cover_image (width: 1000, height: 300,  blur: 10)
      }
    }
  }
}
</static-query>
