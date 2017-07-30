<template>
  <div id="app" v-bind:class="{previewMode: previewMode}">
  <Topbar class='topbar' v-on:preview="preview"/>
    <main>
      <Editor v-bind:resume="resume" class='editor'/>
      <Preview v-bind:resume="resume" class='preview'/>
    </main>
    <el-button id="exitPreview" v-on:click="exitPreview">退出预览</el-button>
  </div>
</template>

<script>
import Topbar from './components/Topbar'
import Editor from './components/Editor'
import Preview from './components/Preview'

export default {
  data() {
    return {
      previewMode: false,
      resume: {
        profile: { name: '', city: '', birth: '' },
        workHistory: [{ company: '', content: '' }],
        studyHistory: [{ school: '', duration: '', degree: '' }],
        projects: [{ name: '', content: '' }],
        awards: [{ name: '' }],
        contacts: [{ qq: '', wechat: '', phone: '', email: '' }]
      }
    }
  },
  methods: {
    exitPreview(){
      this.previewMode = false
    },
    preview(){
      this.previewMode = true
    }
  },
  components: {
    Topbar, Editor, Preview
  },
}

</script>

<style lang='scss'>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    height: 100vh;
    display: flex;
    flex-direction: column;
  }


  .topbar {
    position: relative;
    box-shadow: 0 0 3px hsla(0,0,0,0.5);
    z-index: 1;
  }

  .icon {
    width: 1em; height: 1em;
    vertical-align: -0.15em;
    fill: currentColor;
    overflow: hidden;
  }

  main {
    display: flex;
    flex: 1;
    background: #ddd;

    .editor {
      width: 40em;
      background: #fff;
      margin: 16px 8px 16px 16px;
      box-shadow: 0 0 3px hsla(0,0,0,0.5);
      border-radius: 5px;
      overflow: hidden;
    }

    .preview {
      flex: 1;
      background: #fff;
      margin: 16px 16px 16px 8px;
      box-shadow: 0 0 3px hsla(0,0,0,0.5);
      border-radius: 5px;
    }
  }
  .previewMode {
    > #topbar {
      display: none;
    } 
    
    #editor {
      display: none;
    }

    #preview {
      max-width: 800px;
      margin: 32px auto;
    }

    #exitPreview {
      display: inline-block;
      position: fixed;
      right: 16px;
      bottom: 16px;
    }
  }

  #exitPreview {
    display: none;
  }

</style>
