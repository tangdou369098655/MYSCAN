<template>
  <div class="myhello">
    <x-header :left-options="{backText: ''}" style="background:#eee;">員工健康掃碼</x-header>
    <div class="akd_scan">
        <div class="top">
          <div class="top_one">
            <div class="success">掃碼成功</div>
          </div>
            <div id="mysuccesstime">{{ mydata1 }}</div>
            <img class="myimg" src="../assets/ri2.png" alt="">
        </div>
    </div>
  </div>
</template>

<script>
import { XHeader } from 'vux'

export default {
  name: 'HelloWorld',
  components: {
    XHeader
  },
  data () {
    return {
      mydata1: '2020-02-20 12:40',
    }
  },
  created () {
    this.setDate()
    // this.getData()
  },
  methods: {
    getData () {
      // axios.get('https://lab.ahusmart.com/nCoV/api/overall').then((res) => {
      //   if (res.status === 200) {
      //     const _ = res.data.results[0]
      //     this.confirmedCount = _.confirmedCount
      //     this.suspectedCount = _.suspectedCount
      //     this.curedCount = _.curedCount
      //     this.deadCount = _.deadCount
      //   }
      //   // eslint-disable-next-line no-console
      //   console.log(res)
      // })
    },
    setDate () {
      this.mydata1 = this.getweek()
    },
    getweek (dateString) {
      let da = ''
      if (dateString === undefined) {
        const now = new Date()
        let nowM = now.getMonth() + 1
        // eslint-disable-next-line camelcase
        nowM = nowM < 10 ? '0' + nowM : nowM
        let nowD = now.getDate()
        nowD = nowD < 10 ? '0' + nowD : nowD
        let hour = now.getHours()
        hour = hour < 10 ? '0' + hour : hour
        let minute = now.getMinutes()
        minute = minute < 10 ? '0' + minute : minute
        let second = now.getSeconds()
        second = second < 10 ? '0' + second : second
        da = now.getFullYear() + '-' + nowM + '-' + nowD + ' ' + hour + ':' + minute + ':' + second
      } else {
        da = dateString.toString()
        // 日期格式2015-12-30
      }
      return da;
    }
  }
}
</script>

<style lang="less">
// 標題欄代碼
.myhello /deep/.vux-header .vux-header-left .left-arrow:before {
    border-color:black;
}
.myhello /deep/.vux-header .vux-header-title {
    color: rgb(8, 8, 8);
}
// 標題欄代碼
// 內容代碼
.akd_scan{
  background: linear-gradient(to bottom, #0b68c2, #0b68c2  , #1781cd);
  .top{
    padding-top:1rem;
      position: relative;
    font-size:1.2rem;
    color:white;
    height: 11rem;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    .top_one{
    display: flex;
    justify-content: center;
    margin:1rem;
      .success{
        line-height: 2.5rem;
        width: 10rem;
        color:black;
        background-color: #eff3f4;
      }
    }
    #mysuccesstime{
      font-size:1.5rem;
      margin-bottom: 0.2rem;
    }
    .myimg{
      height: 4rem;
      position: absolute;
    bottom: -1.5rem;
    }
  }
}
// 內容代碼
</style>