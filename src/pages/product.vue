<template>
  <div class="product">
    <product-param>
      <template v-slot:buy>
        <div class="btn" @click="buy">立即购买</div>
      </template>
    </product-param>
    <div class="content">
      <div class="item-bg">
        <h2>小米8</h2>
        <h3>8周年旗舰</h3>
        <p>
          <a href="javascript:;">全球首款双频 GP</a>
          <span>|</span>
          <a href="javascript:;">骁龙845</a>
          <span>|</span>
          <a href="javascript:;">AI 变焦双摄</a>
          <span>|</span>
          <a href="javascript:;">红外人脸识别</a>
        </p>
        <div class="price">
          <span>￥<em>2599</em></span>
        </div>
      </div>
      <div class="item-bg-2">
      </div>
      <div class="item-bg-3">
      </div>
      <div class="item-swiper">
        <swiper :options='swiperOption'>
          <swiper-slide><img src="/img/product/gallery-2.png" alt=""></swiper-slide>
          <swiper-slide><img src="/img/product/gallery-3.png" alt=""></swiper-slide>
          <swiper-slide><img src="/img/product/gallery-4.png" alt=""></swiper-slide>
          <swiper-slide><img src="/img/product/gallery-5.jpg" alt=""></swiper-slide>
          <swiper-slide><img src="/img/product/gallery-6.jpg" alt=""></swiper-slide>
          <div class="swiper-pagniation" slot="pagination"></div>
        </swiper>
        <p class="desc">小米8 AI变焦双摄拍摄</p>
      </div>
      <div class="item-video">
        <h2>60帧超慢动作摄影<br/>慢慢回味每一瞬间的精彩</h2>
        <p>后置960帧电影般超慢动作视频，将眨眼间的美妙展现得淋漓尽致！<br/>更能AI 精准分析视频内容，15个场景智能匹配背景音效。</p>
        <div class="video-bg" @click="showSlide = true"></div>
        <div class="video-box" >
          <div class="overlay" v-if="showSlide">
          </div>
          <div class="video" :class="{'slide':showSlide}">
            <span class="icon-close" @click="showSlide = false"></span>
            <video src="/img/product/video.mp4" controls="controls"></video>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ProductParam from './../components/ProductParam'
import { Swiper as SwiperClass, Pagination, Mousewheel, Autoplay, Navigation ,EffectFade,EffectCoverflow,EffectCube} from 'swiper/core'
import getAwesomeSwiper from 'vue-awesome-swiper/dist/exporter'
import 'swiper/swiper-bundle.min.css'
const { Swiper, SwiperSlide } = getAwesomeSwiper(SwiperClass)
SwiperClass.use([Pagination, Mousewheel, Autoplay,Navigation,EffectFade,EffectCoverflow,EffectCube])
export default {
  name: 'product',
  data() {
    return {
      showSlide:false,
      product:{

      },
      swiperOption:{
        autoplay:true,
        slidesPerView:3,
        spaceBetween:30,
        freeMode:true,
        pagination:{
          el:'.swiper-pagination',
          clickable: true
        }
      }
    }
  },
  components:{
    ProductParam,
    Swiper,
    SwiperSlide
  },
  methods: {
    buy(){
      let id = this.$route.params.id
      this.$router.push(`/detail/${id}`);
    }
  },
}
</script>

<style lang='scss'>
@import './../assets/sass/config';
@import './../assets/sass/mixin';
  .product{
    .content{
      .item-bg{
        background: url('/img/product/product-bg-1.png') no-repeat center;
        height: 718px;
        text-align: center;
        h2{
          font-size: 80px;
          padding-top: 55px;
        }
        h3{
          font-size: 24px;
          letter-spacing: 10px;
        }
        p{
          margin-top: 21px;
          margin-bottom: 40px;
          a{
            font-size: 16px;
            color:#333;
          }
          span{
            margin: 0 15px;
          }
        }
        .price{
          font-size: 30px;
          color:#333;
          em{
            font-style:normal;
            font-size: 38px;
          }
        }
      }
      .item-bg-2{
        background: url('/img/product/product-bg-2.png') no-repeat center;
        height: 480px;
        background-size: 1226px 397px;
      }
      .item-bg-3{
        background:url('/img/product/product-bg-3.png') no-repeat center;
        background-size: cover;
        height: 638px;
      }
      .item-swiper{
        margin: 36px auto 52px;
        .desc{
          font-size: 18px;
          color: #333;
          text-align: center;
        }
        img{
          width: 100%;
        }
      }
      .item-video{
        height: 1044px;
        background-color: #070708;
        margin-bottom: 76px;
        color: #fff;
        text-align: center;
        h2{
          font-size: 60px;
          padding-top: 82px;
          margin-bottom: 47px;
        }
        p{
          font-size: 24px;
          margin-bottom: 58px;
        }
        .video-bg{
          background:url('/img/product/gallery-1.png') no-repeat center;
          background-size: cover;
          width: 1226px;
          height: 540px;
          margin: 0 auto 120px;
          cursor:pointer;
        }
        .video-box{
          .overlay{
            @include position(fixed);
            background-color: $colorB;
            opacity: .4;
            z-index: 2;
          }
          .video{
            position: fixed;
            top:-50%;
            left: 50%;
            transform: translate(-50%,-50%);
            width: 1000px;
            height: 536px;
            z-index: 2;
            opacity: 0;
            transition: all .6s;
            &.slide{
              top: 50%;
              opacity: 1;
            }
            .icon-close{
              position:absolute;
              top:20px;
              right: 20px;
              @include bgImg(20px,20px,'/img/icon-close.png');
              cursor:pointer;
              z-index: 3;
            }
            video{
              width: 100%;
              height: 100%;
              object-fit: cover;
              outline: none;
            }
          }
        }
      }
    }
    .btn{
      margin-left: 10px;
    }
  }
</style>