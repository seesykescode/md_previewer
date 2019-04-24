<template>
  <div class="wrapper">
    <h2>Thing</h2>
    <textarea name="input" id="editor" cols="30" rows="10" v-model="input"></textarea>
    <div class="preview" v-html='markDown'>
      
    </div>
  </div>
</template>

<script>
import marked from 'marked'
export default {
  name: 'Home',
  data () {
    return {
      input: '# hello fellow children  ## welcome to hell.'
    }
  },
  computed: {
    markDown: function () {
      marked.setOptions({
      renderer: new marked.Renderer(),
      grm: true,
      breaks: true,
      sanitize: true,
      smartypants: true,
      tables: true
  })
  return marked(this.input)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
