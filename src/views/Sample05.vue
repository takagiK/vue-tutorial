<template>
  <div class="sample">
    <h1>Sample page</h1>
    <p>---------------------------------------------</p>
    <div>
      <!-- 完全な構文 -->
      <button v-on:click="getMess()"> click </button>
      <!-- 省略記法 -->
      <!-- <button @click="getMess()"> ... </button> -->
      <h2>{{ message }}</h2>
    </div>
  </div>
</template>


<style scoped>
li {
  margin: auto;
  text-align: left;
}
</style>


<script>
export default {
  name: 'Sample',

  // 変数定義
  data() {
    return {
      message: '',
      btnFlg: true
    }
  },

  // 関数
  methods: {
    getMess() {
      if ( this.btnFlg ) {
        this.btnFlg = false;
        this.message = 'click !!!';
      } else {
        this.btnFlg = true;
        this.message = '';
      }
      console.log('on click !')
    }
  }

}
// v-on
</script>
