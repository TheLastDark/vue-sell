<template>
  <div id="app">
    <v-header :seller="seller"></v-header>
    <div class="tab-wrapper">
      <tab :tabs="tabs" :initial-index=0></tab>
    </div>
  </div>
</template>

<script>
import VHeader from 'components/v-header/v-header'
import Tab from './components/tab/tab'
import { getSeller } from 'api'
import Goods from './components/goods/goods'
import Seller from "./components/seller/seller"
import Ratings from './components/ratings/ratings'
import qs from 'query-string'
export default {
  name: 'app',
  data() {
    return {
      seller: {
        id: qs.parse(location.search).id
      }
    }
  },
  computed: {
    tabs() {
      return [
        {
          label: '商品',
          component: Goods,
          data: {
            seller: this.seller
          }
        },
        {
          label: '评价',
          component: Ratings,
          data: {
            seller: this.seller
          }
        },
        {
          label: '商家',
          component: Seller,
          data: {
            seller: this.seller
          }
        }
      ]
    }
  },
  created() {
    //在created钩子函数请求服务器数据
    this._getSeller()
  },
  methods: {
    _getSeller() {
      getSeller({
        id: this.seller.id
      }).then((seller) => {
        this.seller = seller
      })
    }
  },
  components: {
    VHeader,
    Tab,
    Goods,
    Ratings,
    Seller
  }
}
</script>
<style lang="stylus">
 #app
    .tab-wrapper
      position: fixed
      top: 136px
      left: 0
      right: 0
      bottom: 0
</style>
