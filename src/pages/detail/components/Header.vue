<template>
    <div>
      <router-link tag="div" to="/" class="header-abs" v-show="showAbs">
          <div class="icon iconfont icon-fanhui header-abs-back"></div>
      </router-link>
      <div class="header-fixed" v-show="!showAbs" :style="opacityStyle">
        景点详情
        <router-link to="/">
            <div class="icon iconfont icon-fanhui header-fixed-back"></div>
        </router-link>
      </div>
    </div>
</template>
<script>
export default {
  name: 'DetailHeader',
  data () {
    return {
      showAbs: true,
      opacityStyle: {
        opacity: 0
      }
    }
  },
  methods: {
    handleScroll () {
      const top = document.documentElement.scrollTop
      if (top > 60) {
        const opacity = top / 140
        this.opacityStyle = {
          opacity
        }
        this.showAbs = false
      } else {
        this.showAbs = true
      }
    }
  },
  activated () {
    window.addEventListener('scroll', this.handleScroll)
  },
  deactivated () {
    window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>
<style lang="stylus" scoped>
@import '~styles/varibles.styl'
.header-abs
  position absolute
  left .2rem
  top .2rem
  width .8rem
  height .8rem
  border-radius .4rem
  background rgba(0,0,0,.8)
  text-align center
  line-height .8rem
.header-abs-back
  color #fff
  font-size .4rem
.header-fixed
  z-index 2
  position fixed
  top 0
  left 0
  right 0
  height $headerHeight
  line-height $headerHeight
  text-align center
  color #fff
  background $bgColor
  font-size .32rem
.header-fixed-back
  width .64rem
  text-align center
  font-size .4rem
  position absolute
  top 0
  left 0
  color #fff
</style>
