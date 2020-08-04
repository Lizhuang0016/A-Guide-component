<template>
  <div id="app">
    <p>Some text</p>
    <p>Some text</p>
    <p>Some text</p>
    <p>Some text</p>
    <p>Some text</p>
    
    <p>Some other text</p>
    <p>Some other text</p>
    <p>Some other text</p>
    <p>Some other text</p>
    <div class="tipbox"><ShepherdExample/></div>
    <div class="test">我是测试div</div>
    <div class="test1">我是第二个测试div</div>
    
  </div>
</template>


<style lang="less" scoped>
  @import '../demo/assets/shepherd.css';
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: left;
    color: #2c3e50;
    margin-top: 60px;
    outline: 1px solid orange!important;

    
  }
 
  .test{
    width: 200px;
    height: 100px;
    background-color: aquamarine;
  }
  .test1{
    width: 300px;
    height: 200px;
    background-color: aquamarine;
    margin-left: 1200px;
    margin-top:100px;
  }
  .example-step-extra-class{
    width: 200px;
    height: 200px;
    background-color:bisque;
  }
  .testbox{
    color:red;
  }
  /deep/.shepherd-text {
  color: rgba(0, 0, 0, 0.75);
  font-size: 1rem;
  line-height: 1.3em;
  max-height: 30vh;
  padding: 0.75em;
}
</style>
<script>
  import ShepherdExample from './components/ShepherdExample';

  export default {
    components: { ShepherdExample }
  };
</script>
