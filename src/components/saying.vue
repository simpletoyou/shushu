<template>
  <div class="saying-container">
    <!-- 背景图 -->
    <div class="banner" :style="'height:' + winHeight"></div>
    <!-- 导航栏 -->
    <page-header></page-header>

    <!-- 页面主体 -->
    <article>
      <div class="main">
        <div class="bracket-left">『</div>
        <div class="text">{{ says.hitokoto }}</div>
        <div class="bracket-right">』</div>
      </div>
      <div class="from">——&nbsp;{{ says.from }}</div>

    </article>
  </div>
</template>

<script>
// import axios
import axios from "axios"
import pageHeader from './pageHeader.vue'
export default {
  data() {
    return {
      says: {},
      winHeight: '',
    }
  },
  components: {
    pageHeader
  },
  mounted() {
    // 请求一言接口
    let that = this
    that.fun()
    this.winHeight = window.innerHeight + 'px'
    window.setInterval(() => {
      setTimeout(that.fun(), 0)
    }, 5000)
  },
  methods: {
    fun() {
      let that = this
      axios.get('https://v1.hitokoto.cn')
        .then(({
          data
        }) => {
          that.says = data
        })
        .catch(console.error)
    }
  }
}
</script>

<style lang="less">
@line: .3rem;
@color: #FFF;
@bg: #d9d9d9;
@font: .2rem;

.saying-container {
  line-height: @line;
  position: relative;
  color: #FFF;


  // .banner {
  //   filter: brightness(0.6);
  //   width: 100%;
  //   background: url(https://cn-south-227-storage-hitokoto-19627663.oss.dogecdn.com/pic/qf3cu.jpg) center no-repeat;
  //   background-size: cover
  // }

  article {
    position: absolute;
    top: 38%;
    width: 12rem;
    text-align: center;
    display: flex;
    flex-direction: column;
    padding: 0 calc(50% - 6rem);

    .main {
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: .4rem;

      .text {
        padding: 0 .2rem;
        line-height: .8rem;
      }
    }

    .from {
      font-size: .2rem;
      margin-top: .4rem;
    }
  }
}
</style>
