<template>
    <div class="header">
        <div class="header-left">
          <div class="icon iconfont icon-fanhui back-icon"></div>
        </div>
        <div class="header-input">
          <span class="icon iconfont icon-sousuo"></span>
          输入城市/景点/游玩主题
        </div>
        <router-link to="/city">
          <div class="header-right">
            <span class="icon iconfont icon-jiantou arrow-icon"></span>
            {{this.city}}
          </div>
        </router-link>
    </div>
</template>
<script>
import { mapState, mapGetters } from 'vuex'
export default{
  name: 'HomeHeader',
  computed: {
    ...mapState(['city']),
    ...mapGetters(['doubleCity'])
  }
}
</script>
<style lang="stylus" scoped>
@import '~styles/varibles.styl'
.header
  display:flex
  line-height:$headerHeight
  background-color :$bgColor
  color:#fff
.header-left
  width:.64rem
  float:left
.header-input
  flex:1
  background:#fff
  border-radius:.1rem
  margin-top:.12rem
  margin-left:.2rem
  padding-left:.2rem
  height:.64rem
  line-height:.64rem
  color:#ccc
.header-right
  min-width: 1.04rem
  padding 0 .1rem
  float:right
  text-align:center
  color #fff
.back-icon
  text-align:center
  font-size:.4rem
.arrow-icon
  font-size:.24rem
  margin-left:-.04rem
</style>
