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
      input: `
      
# Markdown Previewer
## Created by Johnathon Sykes

____

### Emphasis and Italics

You want to make a bold statement? Use double asterisks surrounding your text.

**Like this** 

Need to italicize your text Juse use single astericks surronding your text.

*Like this*
____

### Code in Markdown

Standalone elements can be typed with a a pair of backticks

\`<h2>See, no formatting on me\`

Here's a code block, I'm working on getting syntax highlighting working.

\`\`\`\ javascript
function fancyAlert(arg) {
  if(arg) {
    $.facebox({div:'#foo'})
  }
}
\`\`\`\
____

### Lists

Here's how you create a list in markdown

#### Ordered

1. Thing
2. Thing 2
3. Thing 3.

#### Unordered list

* Thing
* Another Thing
* 3rd Thing's a charm

Just like that. Cool, right
____

### Blockquotes

Use a \`>\` in front of your text in order to create a block text

> Because **WE** are your friends
> **YOU'LL** never be alone again
> Well come on!
> Well come on!
> Well come on!
____

### Links

Links can be created by using the following syntax

\`[<link text>](<URL>)\`

Check this link out!
[My favorite soccer team](http://www.lagalaxy.com)
____

### Images

Image syntax is pretty similar to links but with one big difference...well character

\`![<alt text of image>](<image URL>)\`

![You win...Markdown!](https://media.giphy.com/media/3oEduGdxEVeRU3fijC/giphy.gif)
      `
    }
  },
  computed: {
    markDown: function () {
      marked.setOptions({
      renderer: new marked.Renderer(),
      gfm: true,
      tables: true,
      breaks: true,
      sanitize: true,
      smartLists: true,
      smartypants: false
  })
  return marked(this.input)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
