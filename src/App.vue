<template>
  <div id="app">
    <br><br><br>
    <h2 :class="classAttr">Example Font for teaching Purpose</h2>
    <br><br><br>
    <label for="">.{{classAttr}}</label>
    <textarea name="" v-model="styles" id="" cols="30" rows="10"></textarea>
  </div>
</template>

<script>
export default {
  name: 'app',
  mounted() {
      this.setUpStyles();
  },
  watch: {
    styles(){
      document.head.getElementsByTagName('style')[1].remove();
      this.setUpStyles();
    },
    classAttr(){
      this.setUpStyles();
    }
  },
  data () {
    return {
      styles:
`{

color: red;

}`,
      classAttr: 'myClass'
    }
  },
  methods: {

    setUpStyles() {
      let style = document.createElement('style')
      style.type = "text/css"
      style.appendChild(document.createTextNode(''))
      this.styleNode = style.childNodes[0] // a reference I store in the data hash
      style.innerHTML = '.' + this.classAttr + this.styles;
      document.head.appendChild(style)

    }
  }
}
</script>

<style>
  h2{
    text-align: center;

  }
  textarea, input{
    padding: 10px;
    font-family: 'Courier New', Courier, monospace;
    border: none;
  }
  label{
    font-weight: bold;
    display: block;
    margin-bottom: 10px;
  }
  textarea{
    background: #eee;
    width: 98%;
    box-shadow: 0px 0px 1px black;
    line-height: 14pt;
  }
  input{
    padding: 10px;
    margin: 20px 0;
    border-bottom: thin solid black;
  }
  label{
  }
</style>
