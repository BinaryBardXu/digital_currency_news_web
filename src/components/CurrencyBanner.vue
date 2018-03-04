<template>
        <div class="currency-banner">
          <div class='currency-market' v-for="(ticker,index) of tickers" :key="index">
            <span>币种:{{ ticker.symbol }}</span>
            <span>美元:${{ ticker.price_usd }}</span>
            <span>人民币:{{ ticker.price_cny }}</span>
            <span>1小时涨幅:<span  v-bind:class="{ 'amount-increase': ticker.percent_change_1h > 0, 'amount-decrease': ticker.percent_change_1h < 0 }">{{ ticker.percent_change_1h }}</span></span>
            <span>24小时涨幅:<span  v-bind:class="{ 'amount-increase': ticker.percent_change_24h > 0, 'amount-decrease': ticker.percent_change_24h < 0 }">{{ ticker.percent_change_24h }}</span></span>
            <span>7日内涨幅:<span  v-bind:class="{ 'amount-increase': ticker.percent_change_7d > 0, 'amount-decrease': ticker.percent_change_7d < 0 }">{{ ticker.percent_change_7d }}</span></span>
          </div>
        </div>
</template>

<script>
import axios from 'axios'

export default {
  data () {
    return {
      tickers: [],
      time: 60 * 30,
      errors: []
    }
  },
  // Fetches posts when the component is created.
  created () {
    this.loadCurrencyMarket()
    this.timer = setInterval(this.loadCurrencyMarket, 300000)
  },
  methods: {
    loadCurrencyMarket: function () {
      axios.get(`https://api.coinmarketcap.com/v1/ticker/bitcoin/?convert=CNY`)
        .then(response => {
          this.tickers.push(response.data[0])
        })
        .catch(e => {
          this.errors.push(e)
        })
      axios.get(`https://api.coinmarketcap.com/v1/ticker/ethereum/?convert=CNY`)
        .then(response => {
          this.tickers.push(response.data[0])
        })
        .catch(e => {
          this.errors.push(e)
        })
    },
    cancelAutoUpdate: function () { clearInterval(this.timer) }
  },
  beforeDestroy () {
    clearInterval(this.timer)
  }
}
</script>
<style>
.currency-banner {
    background-color:  white;
    width: 100%;
    height:  30px;
    line-height:  30px;
    font-size:  12px;
    text-align:  center;
    margin:  auto;
    position: fixed;
    z-index: 9999;
}

.currency-market {
    float:  left;
    width: 50%;
    margin: auto;
}

.currency-market span {
    margin-left: 10px;
}
.amount-increase{
  color: green
}
.amount-decrease{
  color: red
}
</style>
