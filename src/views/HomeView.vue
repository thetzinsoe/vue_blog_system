<template>
  <div>
    <h3 v-if="error">{{ error }}</h3>
    <span v-else class="tagcloud">
      <PostList :posts="posts"></PostList>
      <TagCloud :posts="posts"></TagCloud>
    </span>
  </div>
</template>

<script>
import TagCloud from "../components/TagCloud";
import getPost from "../composables/getPosts";
import PostList from "../components/PostList.vue";
export default {
  name: "HomeView",
  components: {
    TagCloud,
    PostList,
  },
  setup() {
    let { posts, load, error } = getPost();
    load();
    return { posts, error };
  },
};
</script>
<style>
div {
  overflow-y: hidden;
}
.tagcloud {
  max-width: 800px;
  display: grid;
  grid-template-columns: 3fr 1fr;
  gap: 10px;
}
</style>
