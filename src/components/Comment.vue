<template>
  <div class="comment">
    <h3>Comment from {{ comment.author }}</h3>
    <p>{{ comment.text }}</p>
  </div>
</template>

<script>
export default {
  data () {
    return {
      comment: {}
    }
  },
  mounted () {
    this.$http.get('http://localhost:3000/api/comments/' + this.$route.params.id).then(
      (response) => {
        this.comment = response.body
      },
      (response) => {

      }
    )
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  color: #42b983;
}
</style>
