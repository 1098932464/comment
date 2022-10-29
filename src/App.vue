<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <div id="div" contenteditable="true" @input="oninput" class="comment">
      {{value}}
    </div>
  </div>
</template>

<script>


export default {
  name: 'App',
  data(){
    return {
      value:'啊啊啊啊啊啊啊啊'
    }
  },
  mounted(){
  let selection =  window.getSelection()
    var range = document.createRange();
    console.log(document.getElementById('div'));
    range.selectNodeContents(document.getElementById('div'));
       selection.addRange(range)
       selection.collapseToEnd()
  },
  methods:{
    oninput(e){
      // 移动光标到末尾
    let selection =  window.getSelection()
    var range = document.createRange();
    range.selectNodeContents(e.target);
// console.log(e.target);
let text = e.target.innerText
console.log(text);
// range.collapse(false);

// range.setStart(e.target, 0);
// range.setEnd(e.target, text.length-2);
selection.removeAllRanges();
    selection.addRange(range)
    console.log(selection);
    // selection.collapseToEnd()

    }
  }
}
</script>

<style >
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;

}
  .comment{
    border: 1px solid #ddd;
  }
</style>
