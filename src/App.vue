<template>
  <div id="app" class="clearfix">
    <div class="align-right">
      <div class="viewport">
        <h2 :class="classAttr">[h2] Example Font for teaching Purpose</h2>
        <span>[span] This is a span</span>

        <section>
          <h3>[h3] this is a headline3, below ul[class=list][id=list]</h3>
          <ul class="list">
            <li>List Item</li>
            <li>List Item</li>
            <li>List Item</li>
            <li>List Item</li>
            <li>List Item</li>
          </ul>
        </section>

        <section>
          <h3>[h3] this is a headline3, below div[class=container]</h3>

          <div class="container"></div>
          <div class="container"></div>
        </section>

        <figure>
          <img src="./assets/logo.png" alt="This is an image" title="vuejs Logo">
          <figcaption>figure>img+figcation</figcaption>
        </figure>
      </div>
    </div>
    <div class="align-left">
      <textarea name="" contenteditable="true" v-model="styles" id="" cols="30" rows="10"></textarea>
    </div>
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
      classAttr: 'headline',
      styles:
`.headline{
  font-family: Arial, sans-serif;
}

.container{
  height: 100px;
  width: 100px;
  background: red;
  margin: 10px auto;
}`,
    }
  },
  methods: {

    setUpStyles() {
      let style = document.createElement('style')
      style.type = "text/css"
      style.appendChild(document.createTextNode(''))
      this.styleNode = style.childNodes[0] // a reference I store in the data hash
      style.innerHTML = this.styles;
      document.head.appendChild(style)

    }
  }
}
</script>

<style>
  h2{
    text-align: center;
    font-size: 24px;
  }

  .clearfix:after{
    content: ' ';
    height: 0;
    visibility: none;
    clear: both;
  }
  textarea, input{
    padding: 10px;
    font-family: 'Courier New', Courier, monospace;
    border: none;
    height: 93vh;
  }
  label{
    font-weight: bold;
    display: block;
    margin-bottom: 10px;
  }
  textarea{
    background: #eee;
    box-shadow: 0px 0px 1px black;
    line-height: 14pt;
    width: 28%;
    position: fixed;
  }
  input{
    padding: 10px;
    margin: 20px 0;
    border-bottom: thin solid black;
  }
  .viewport{
    width: 100%;
  }
  .align-left{
    float: left;
    width: 30%;
  }
  .align-right{
    float: right;
    width: auto;
    text-align: center;
    width: 70%;
    height: 98vh;
  }
  section, figure{
    border: thin solid black;
    padding: 10px;
    margin: 10px;

  }
  ul li{
    list-style-type: none;
    line-height: 18pt;
  }
</style>
