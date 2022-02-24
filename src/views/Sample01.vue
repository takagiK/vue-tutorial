<template>
  <div class="sample">
    <h1>Sample page</h1>
  </div>
</template>


<style scoped>
div {
  background-color: skyblue;
}
</style>


<script>
export default {
  name: 'Sample',
  
  // =========================
  // 変数定義
  data() {
    return {
      message: 'hello !'
    }
  },

  // =========================
  // 関数
  methods: {
    getMess() {
      console.log('get message !')
    }
  }
}
// sample
</script>



