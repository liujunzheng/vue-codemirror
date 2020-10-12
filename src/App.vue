<template>
  <div id="app">
    <button @click='onAddCodeItem'>继续新增</button>
    <div class="code-mirr-item" :key='codeIndex' v-for='(codeItem, codeIndex) in codeContentList'>
      <codemirror
        class='codemirror-item'
        :options='options'
        v-model='codeItem.value'></codemirror>
    </div>
  </div>
</template>

<script>
import {
  codemirror
} from 'vue-codemirror-lite'
require('codemirror/mode/shell/shell')
require('codemirror/theme/material-darker.css')
export default {
  name: 'app',
  data () {
    return {
      codeContentList: [
        {
          value: '#!/usr/bin/bash\n'
        },
        {
          value: '#!/usr/bin/bash\necho "test" \n'
        }
      ],
      options: {
        mode: 'shell',
        theme: 'material-darker',
        lineNumbers: true,
        lineWrapping: true
      }
    }
  },
  components: {
    codemirror
  },
  methods: {
    onAddCodeItem () {
      this.codeContentList.push({
        value: ''
      })
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
.code-mirr-item{
  border: 1px solid #ddd;
  height: 100px;
}
.vue-codemirror-wrap,
.cm-s-material-darker.CodeMirror{
  height: 100%;
}
</style>
