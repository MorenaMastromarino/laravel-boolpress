<template>
  <div class="container single-post">
    <h3>Titolo</h3>
    <p class="category">categoria</p>
    <div>
      <span class="tag">tag</span>
    </div>
    <p class="date" >00/00/0000</p>
    <p class="text">contenuto</p>
  </div>
</template>

<script>
export default {
  name: 'PostDetail',

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