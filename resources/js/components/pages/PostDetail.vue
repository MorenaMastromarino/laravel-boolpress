<template>
  <div class="container single-post">
    <h2>{{post.title}}</h2>
    <p v-if="post.category" class="category">{{post.category.name}}</p>

    <div v-if="post.tags">
      <span
       class="tag"
        v-for="(tag, index) in post.tags"
        :key="`tag${index}`"
      >{{tag.name}}</span>
    </div>

    <p class="text">{{post.content}}</p>
  </div>
</template>

<script>
export default {
  name: 'PostDetail',

  data(){
    return {
      apiUrl: 'http://127.0.0.1:8000/api/posts/',
      post: {
        title: '',
        category: {},
        tags: [],
        content: '',

      }
    }
  },

  mounted(){
    this.getApi();
  },

  methods: {
    getApi(){
      axios.get(this.apiUrl + this.$route.params.slug)
      .then(res => {
        this.post = res.data;
        console.log(this.post);
      })
    }
  }
}
</script>

<style lang="scss" scoped>
  .single-post {
    padding: 10px 0;
    .category {
      color: gray;
    }
    .tag {
      display: inline-block;
      font-size: 12px;
      background-color: #0492f0;
      color: white;
      border-radius: 4px;
      padding: 2px 4px;
      margin-right: 5px;
    }
    .date {
      font-size: 12px;
      font-style: italic;
    }
    
  }
</style>