<template>
  <header>
   <nav>
     <ul>
       <li><a href="#">Home</a></li>
       <li><a class="active" href="#">Blog</a></li>
       <li><a href="#">Chi siamo</a></li>
       <li><a href="#">Contatti</a></li>
     </ul>
   </nav>
  </header>
</template>

<script>
export default {
  name: 'Header',
}
</script>

<style lang="scss" scoped>
  header {
    background-color: #007ACC;
    text-align: center;
    padding: 10px 0;
    ul {
      list-style: none;
      li {
        display: inline-block;
        margin: 0 10px;
        a {
          color: white;
          text-decoration: none;
          &.active {
            color: aqua;
          }
          &:hover{
            text-decoration: underline;
          }
        }
      }
    }
  }
</style>