<template>
  <div class="sample">
    <h1>Sample page</h1>
    <p>---------------------------------------------</p>
    <div>
      <ul>
        <li  v-for="(item) in colors" v-bind:key="item.color">
          <input type="checkbox" :value=item.color v-model="checkedColor">
          <label>{{ item.color }}</label>
        </li>
      </ul>
      <span>{{ checkedColor }}</span>
    </div>
    <br><br>
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
      colors: [ 
        {color: 'red'},
        {color: 'yellow'},
        {color: 'blue'}
      ],
      checkedColor: []
    }
  }

}
// v-for
</script>
