<template>
  <div class="test">
    <h1>Hello App!</h1>
    <p>
      <!-- 使用 router-link 组件来导航. -->
      <!-- 通过传入 `to` 属性指定链接. -->
      <!-- <router-link> 默认会被渲染成一个 `<a>` 标签 -->
      <router-link to="/foo">Go to Foo</router-link>
      <router-link to="/bar">Go to Bar</router-link>
    </p>
    <router-view>
      <h2>Hello again?</h2>
      <ul>
        <li v-for="comment in comments">{{ comment.text }}</li>
      </ul>
    </router-view>
  </div>
</template>

<script>
import $ from 'jquery'

export default {
  data () {
    return {
      comments: []
    }
  },
  mounted () {
    $.ajax({
      url: 'http://localhost:3000/api/comments',
      dataType: 'json',
      type: 'GET',
      success: function (data) {
        this.comments = data
      }
    })
  }
}
</script>

<style>
html {
  height: 100%;
}

body {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
}

#app {
  color: #2c3e50;
  margin-top: -100px;
  max-width: 600px;
  font-family: Source Sans Pro, Helvetica, sans-serif;
  text-align: center;
}

#app a {
  color: #42b983;
  text-decoration: none;
}

.logo {
  width: 100px;
  height: 100px
}
</style>
