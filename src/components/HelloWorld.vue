<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <button v-on:click="flipA"> flipA</button>
    <button v-on:click="flipB"> flipB</button>
    <Message
      v-bind:mess="msg"
      v-bind:disabledSubmit="!rangeHasChanged"
    ></Message>
  </div>
</template>

<script>
import Message from './Message.vue'
const HelloWord = {
  name: 'HellowWord',
  components: {
    Message
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      A: true,
      B: true
    }
  },

  methods: {
    flipA () {
      console.log('clicked A')
      this.A = !this.A
    },
    flipB () {
      console.log('clicked B')
      this.B = !this.B
    }
  },

  computed: {
    rangeHasChanged () {
      const A = this.A
      const B = this.B
      console.log('range is')
      console.log(A || B)
      return A || B
    }
  }
}

export default HelloWord
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
