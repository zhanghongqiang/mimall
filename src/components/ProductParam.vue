<template>
  <div class="nav-bar" :class="{isFix:isFixed}">
    <div class="container">
      <div class="pro-title">
        小米8
      </div>
      <div class="pro-param">
        <a href="javascript:;">参数</a><span>|</span>
        <a href="javascript:;">概述</a><span>|</span>
        <a href="javascript:;">用户评价</a>
        <slot name="buy"></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name:'ProductParam',
  data() {
    return {
      isFixed:false
    }
  },
  mounted() {
    window.addEventListener('scroll',this.initHeight);
  },
  methods: {
    initHeight(){
      let scrollTop = window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop;
      this.isFixed = scrollTop > 152 ? true : false;
    }
  },
  destroyed() {
    window.removeEventListener('scroll',this.initHeight,false);
  },
}
</script>

<style lang="scss" scoped>
@import './../assets/sass/config';
@import './../assets/sass/mixin';
  .nav-bar{
    height: 70px;
    line-height: 70px;
    border-top:1px solid $colorH;
    &.isFix{
      position: fixed;
      top: 0;
      width: 100%;
      background-color: $colorG;
      box-shadow: 0 5px 5px rgba(0,0,0, .07);
      z-index: 2;
    }
    .container{
      @include flex();
      .pro-title{
        font-size: $fontH;
        color:$colorB;
        font-weight: bold;
      }
      .pro-param{
        font-size: $fontJ;
        a{
          color:$colorC;
        }
        span{
          margin: 0 10px;
        }
      }
    }
  }
</style>