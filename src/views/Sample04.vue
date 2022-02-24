<template>
  <div class="sample">
    <h1>Sample page</h1>
    <p>---------------------------------------------</p>
    <div>
      <div v-if="color === 'red'" style="height:100px; background-color:red">
        red
      </div>
      <div v-else-if="color === 'yellow'" style="height:100px; background-color:yellow">
        yellow
      </div>
      <div v-else-if="color === 'blue'" style="height:100px; background-color:blue">
        blue
      </div>
      <div v-else>
        Not color
      </div>
    </div>
    <p>---------------------------------------------</p>
    <div>
      <button v-on:click="showFoo()"> click </button>
      <div v-show="fooFlg" style="height:100px; background:skyblue">skyblue</div>
    </div>
  </div>
</template>


<style scoped>
</style>


<script>
export default {
  name: 'Sample',

  // 変数定義
  data() {
    return {
      color: 'red',
      fooFlg: true,
    }
  },

  // 関数
  methods: {
    showFoo() {
      if ( this.fooFlg ) {
        this.fooFlg = false;
      } else {
        this.fooFlg = true;
      }
      console.log('on click !')
    }
  }

}
// v-if, v-show
</script>
