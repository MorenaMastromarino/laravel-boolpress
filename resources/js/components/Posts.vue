<template>
  <main>
    <div class="container">
      <h2>Elenco post:</h2>

      <div v-if="posts">
        <PostItem 
          v-for="post in posts"
          :key="`post${post.id}`"
          :post = "post" />

        <div>
          <button
            @click="getPosts(pagination.current - 1)"
            :disabled="pagination.current === 1"
          > << </button>

          <button
            v-for="i in pagination.last"
            :key="`button${i}`"
            @click="getPosts(i)"
            :disabled="pagination.current === i"
          >{{i}}</button>

          <button
            @click="getPosts(pagination.current + 1)"
            :disabled="pagination.current === pagination.last"
          > >> </button>
        </div>

      </div>

      <div v-else>
        <h3>Loading...</h3>
      </div>
    </div>
  </main>
</template>

<script>
import PostItem from './partials/PostItem.vue'

export default {
  name: 'Posts',
  components: {
    PostItem,
  },

  data(){
    return {
      apiUrl: 'http://127.0.0.1:8000/api/posts?page=',
      posts: null,
      pagination: {}
    }
  },
  
  mounted(){
    this.getPosts();
  },

  methods: {
    getPosts(page = 1){
      this.posts = null;
      axios.get(this.apiUrl + page)
      .then( res => {
        this.posts = res.data.data;

        this.pagination = {
          current: res.data.current_page,
          last: res.data.last_page,
        }

        console.log(this.pagination);
      })
    }
  }
}
</script>

<style lang="scss" scoped>
  main{
    padding: 20px 0;
    margin-bottom: 50px;
    button {
      cursor: pointer;
      padding: 5px;
      margin: 0 2px;
    }
  }
</style>