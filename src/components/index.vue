<template>
  <div class="index-container">
    <!-- 导航栏 -->
    <page-header></page-header>
    <article>
      <div class="intro">
        <div class="imgBox">
          <img src="../assets/index/intro1.jpg" alt="">
        </div>
        <div class="infoBox">
          <div class="name">书书</div>
          <div class="desc">Keep running.</div>
          <div class="other">
            Chaos is not a pit, Chaos is a ladder. Many who try to climb it fail, and never get to try again, The fall
            breaks them. And some are given a chance to climb, but they refuse. They cling to the realm, or the gods, or
            love: illusions. Only the ladder is real; the climb is all there is.
          </div>
        </div>
      </div>
      <div class="currentDate">{{ currentDate }}</div>
      <div class="menuBox">
        <div class="card" v-for="(item, index) in cards" :key="index" :class="index == 1 ? 'reserveFlex' : ''">
          <img :src="item.img" alt="">
          <div class="cardInfo">
            <div class="title">{{ item.title }}</div>
            <div class="desc">{{ item.desc }}</div>
            <div class="entryBtn">
              <img src="../assets/index/entry.png" alt="">
            </div>
          </div>
        </div>
      </div>
    </article>
    <!-- 公共尾部 -->
    <page-footer></page-footer>
  </div>
</template>

<script>
import pageHeader from "./pageHeader.vue";
import pageFooter from "./pageFooter.vue";
export default {
  name: "index",
  data() {
    return {
      currentDate: '',
      cards: [
        {
          img: require('../assets/index/rolls.jpg'),
          title: '学习',
          desc: 'I still keep thinking about how an entire life can seemingly amount to nothing. I guess the sad truth is, not everyone will accomplish something great.  Some of us may just have to find meaning in the little moments that make up life.'
        },
        {
          img: require('../assets/index/cups.jpg'),
          title: '生活',
          desc: 'I still keep thinking about how an entire life can seemingly amount to nothing. I guess the sad truth is, not everyone will accomplish something great.  Some of us may just have to find meaning in the little moments that make up life.'
        },
        {
          img: require('../assets/index/plant.jpg'),
          title: '句子',
          desc: 'I still keep thinking about how an entire life can seemingly amount to nothing. I guess the sad truth is, not everyone will accomplish something great.  Some of us may just have to find meaning in the little moments that make up life.'
        }
      ]
    };
  },
  components: {
    pageHeader,
    pageFooter,
  },
  mounted() {
  },
  async created() {
    this.getDate()
    this.subPageData1 = this.$datas.subPageData1;
    this.subPageData2 = this.$datas.subPageData2;
  },
  methods: {
    // 获取当前日期
    getDate() {
      //获取当前的年月日
      let date_ = new Date();
      let y = date_.getFullYear();
      let m = date_.getMonth() + 1;
      let d = date_.getDate();
      this.currentDate = `${y}-${m < 10 ? '0' + m : m}-${d < 10 ? '0' + d : d}`
    },
    toPage(index) {
      index += 1
      if (index===1) {
        // 学习
        this.$router.push('/learning')
      } else if (index ===2) {
        // 生活
        this.$router.push('/life')
      } else {
        // 句子
        this.$router.push('/saying')
      }
    }
  },
};
</script>

<style lang="less">
@themeColor: #5c917b;
@lightTheme: #9ecfba;

.index-container {
  display: flex;
  flex-direction: column;

  article {
    width: 100%;
    padding: 2rem 0;

    .intro {
      display: flex;
      align-items: flex-start;
      justify-content: space-between;
      width: 12rem;
      margin: 0 auto;

      .imgBox {
        width: 4rem;
        height: 4rem;
        margin-right: .5rem;

        img {
          width: 100%;
          height: 100%;
        }
      }

      .infoBox {
        position: relative;
        width: 7.5rem;

        .name {
          margin-top: 1.5rem;
          font-size: .4rem;
          line-height: 1rem;
        }

        .desc {
          font-size: .2rem;
          line-height: 1rem;

        }

        .other {
          line-height: .32rem;
        }

        .line {
          background: #43447a;
          width: 10rem;
          height: .1rem;
          position: absolute;
          right: 0;
          bottom: 0;
          transform: rotate(-45deg);
        }
      }
    }

    .currentDate {
      width: 100%;
      padding: 1.5rem 0;
      margin: 2rem 0;
      background: #FFF;
      color: @themeColor;
      font-size: .6rem;
      text-align: center;
    }

    .menuBox {
      display: flex;
      flex-direction: column;
      width: 12rem;
      margin: 0 auto;

      .card {
        display: flex;
        align-items: stretch;
        justify-content: space-between;

        img {
          width: 6.5rem;
          height: auto;
        }

        &.reserveFlex {
          flex-flow: row-reverse;
        }

        .cardInfo {
          width: 5.5rem;
          padding: 0 .5rem;
          color: #FFF;
          display: flex;
          align-items: flex-start;
          justify-content: center;
          flex-direction: column;

          .title {
            font-size: .4rem;
            width: 100%;
            margin-bottom: .4rem;
          }

          .desc {
            line-height: .32rem;
          }

          // img {
          //   margin: .4rem 0;
          //   width: .4rem;
          //   height: .4rem;
          // }

          .entryBtn {
            color: #fff;
            border-radius: 4px;
            padding: .1rem .6rem;
            margin-top: .4rem;
            font-family: 'Lato', sans-serif;
            font-weight: 500;
            background: transparent;
            cursor: pointer;
            transition: all 0.3s ease;
            position: relative;
            display: inline-block;
            box-shadow: inset 2px 2px 2px 0px rgba(255, 255, 255, .5),
              7px 7px 20px 0px rgba(0, 0, 0, .1),
              4px 4px 5px 0px rgba(0, 0, 0, .1);
            outline: none;

            background-color: #89d8d3;
            background-image: linear-gradient(315deg, #89d8d3 0%, #03c8a8 74%);
            border: none;
            z-index: 1;
            display: flex;
            align-items: center;
            justify-content: center;
            img {
              width: .2rem;
              height: .2rem;
            }

          }

          .entryBtn:after {
            position: absolute;
            content: "";
            width: 100%;
            height: 0;
            bottom: 0;
            left: 0;
            z-index: -1;
            border-radius: 4px;
            background-color: #4dccc6;
            background-image: linear-gradient(315deg, #4dccc6 0%, #96e4df 74%);
            box-shadow:
              -7px -7px 20px 0px #fff9,
              -4px -4px 5px 0px #fff9,
              7px 7px 20px 0px #0002,
              4px 4px 5px 0px #0001;
            transition: all 0.3s ease;
          }

          .entryBtn:hover {
            color: #fff;
          }

          .entryBtn:hover:after {
            top: 0;
            height: 100%;
          }

          .entryBtn:active {
            top: 2px;
          }

        }

      }
    }
  }
}
</style>
