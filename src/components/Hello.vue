<template>
  <div class="hello">
     <editor id="editor_id" height="500px" width="700px" :content="editorText"
            pluginsPath="/static/kindeditor/plugins/"
            :loadStyleMode="false"
            @on-content-change="onContentChange"></editor>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
       editorText: ''
    }
  }, 
  methods: {
    onContentChange (val) {
      this.editorText = val
    }
  }
}
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
