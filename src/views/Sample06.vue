<template>
  <div>
      <b-form>
        <label>郵便番号を入力してください</label>
        <b-input-group class="mb-3">
          <b-row>
            <b-col cols="1" class="ml-5 mr-2"><label>〒</label></b-col>
            <b-col cols="2" class="px-0">
              <b-form-input type="text" v-model="zipCodeTop" />
            </b-col>
            <b-col cols="1" class="mx-0"><label>-</label></b-col>
            <b-col cols="3" class="px-0">
              <b-form-input type="text" v-model="zipCodeBottom" />
            </b-col>
          </b-row>
        </b-input-group>
      </b-form>
      <label>{{ address }}</label>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        zipCodeTop: '',
        zipCodeBottom: '',
        address: ''
      }
    },

    // ===============================================================

    watch: {
      zipCodeTop: function() {
        this.getAddress();
      },
      zipCodeBottom: function() {
        this.getAddress();
      }
    },

    // ===============================================================

    methods: {
      // 郵便番号検索API
      getAddress() {
        // 郵便番号の上の桁数が3以外、下の桁数が4以外なら、処理を中止
        if (this.zipCodeTop.length !== 3 || this.zipCodeBottom.length !== 4) {
          return;
        }
        console.log(this.zipCodeTop, this.zipCodeBottom, `https://zipcloud.ibsnet.co.jp/api/search?zipcode=${this.zipCodeTop}${this.zipCodeBottom}`);
        this.axios
          .get(`https://zipcloud.ibsnet.co.jp/api/search?zipcode=${this.zipCodeTop}${this.zipCodeBottom}`)
          .then(response => {
            console.log(response);
            // 住所データ取得
            const info = response.data.results[0];
            this.address = info.address1 + info.address2 + info.address3;
          })
          .catch(error => {
            console.log(error)
            this.errored = true
          })
          .finally(() => { this.loading = false })
      }
    }
  }
  // axios
</script>