<template>
  <div class="kadai">

    <!-- 課題２ -->
    <!-- 
    <h1>kadai</h1>
    <div>
      <input type="text" v-model="city">
      <button v-on:click="onBtn()"> クリック </button>
      <br>
      <label v-show="onBtnFlg">{{ city }}</label>
    </div> -->


    <!-- 課題３ -->
    <h1>天気予報API</h1>
    <br>
    <div>
      <label>都市ナンバー：</label>
      <input type="text" v-model="city">
      <button v-on:click="getWeather()"> 検索 </button>
    </div>
    <br><br>
    <hr>
    <h3>{{ cityTitle }}</h3>
    <h3>{{ cityName }}</h3>
    <br>
    <h3>~ 明日の天気 ~</h3>
    <br>
    <h4>{{ cityWeather }}</h4>
    <img v-bind:src="imageSrc" alt="天気のイラスト" title="天気のイラスト">
    <br>
    <br>
    <div>
      <p>詳しくは ↓<br>
        <a v-bind:href="cityLink">{{ cityLink }}</a>
      </p>
    </div>
    <br><br><br><hr>
    <br>
    <p>{{ info }}</p>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        city: '',
        // onBtnFlg: false,
        info: [],
        cityName: '',
        cityTitle: '',
        cityLink: '',
        cityWeather: '',
        imageSrc: ''
      }
    },

    // ===============================================================

    methods: {
      // 課題２
      // onBtn() {
      //   if ( this.onBtnFlg ) {
      //     this.onBtnFlg = false;
      //   } else {
      //     this.onBtnFlg = true;
      //   }
      //   console.log('click !')
      // },

      // *********************************************

      // 天気予報API取得
      getWeather() {
        // パラメータの桁数チェック
        if (this.city.length !== 6) {
          return
        }
        // console.log(`https://weather.tsukumijima.net/api/forecast?city=${this.city}`)
        this.axios
          .get(`https://weather.tsukumijima.net/api/forecast?city=${this.city}`)
          .then(response => {
            this.info = response['data']
            console.log(this.info)
            this.cityName = this.info['publishingOffice']
            this.cityTitle = this.info['title']
            this.cityLink = this.info['link']
            this.cityWeather = this.info['forecasts'][0]['telop']
            this.imageSrc = this.info['forecasts'][0]['image']['url']
          })
          .catch(error => {
            console.log(error)
            this.errored = true
          })
          .finally(() => { this.loading = false })
      }
    }
  }
</script>