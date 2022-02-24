<template>
  <div class="sample">
    <h1>Sample page</h1>
    <p>---------------------------------------------</p>
    <div>
      <h2>{{ message }}</h2>
      <input type="text" v-model="message">
    </div>
    <br><br>
    <p>---------------------------------------------</p>
    <div class="checked">
      <ul>
        <li stye>
          <input type="checkbox" id="red" value="red" v-model="checkedColor">
          <label for="red">red</label>
        </li>
        <li>
          <input type="checkbox" id="yellow" value="yellow" v-model="checkedColor">
          <label for="yellow">yellow</label>
        </li>
        <li>
          <input type="checkbox" id="blue" value="blue" v-model="checkedColor">
          <label for="blue">blue</label>
        </li>
      </ul>
      <span>{{ checkedColor }}</span>
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

  // =========================
  // 変数定義
  data() {
    return {
      message: 'hello !',
      checkedColor: []
    }
  }

}
// v-model
</script>
