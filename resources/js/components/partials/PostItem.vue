<template>
  <article>
    <h3>
      <a href="#">{{post.title}}</a>
    </h3>
    <p class="category" v-if="post.category">{{post.category.name}}</p>
    <div v-if="post.tags">
      <span
       class="tag"
        v-for="tag in post.tags"
        :key="`tag${tag.id}`"
      >{{tag.name}}</span>
    </div>

    <p class="date" >{{formatData}}</p>
    <p class="text">{{troncateText}}</p>
  </article>
</template>

<script>
export default {
  name: 'PostItem',
  props: {
    'post': Object
  },
  computed: {
    troncateText(){
      return this.post.content.substr(0, 50) + '...';
    },
    formatData(){
      const d = new Date(this.post.created_at);
      let day = d.getDay();
      let month = d.getMonth() +1;
      const year = d.getFullYear();

      if(day < 10){
        day = '0' + day;
      }

      if(month < 10){
        month = '0' + month;
      }

      return `${day}/${month}/${year}`;
    }
  }
}
</script>

<style lang="scss" scoped>
  article {
    padding: 10px 0;
    a {
      color: black;
      text-decoration: none;
      &:hover {
        text-decoration: underline;
      }
    }
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