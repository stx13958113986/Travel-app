<template>
    <div class="list" ref="wrapper">
      <div>
       <div class="area">
          <div class="title border-topbottom">当前城市</div>
          <div class="button-list">
             <div class="button-wrapper" v-for="item of hot" :key="item.id">
               <div class="button">
                  {{item.name}}
               </div>
             </div>
          </div>
       </div>
      <div class="area" v-for="(item,key) of city" :key="item.id">
          <div class="title border-topbottom" >{{key}}</div>
          <div class="item-list">
             <div class="item border-bottom" v-for="innerItem of item" :key="innerItem.id">{{innerItem.name}}</div>
          </div>
       </div>
      </div>
    </div>
</template>
<script>
import BScroll from 'better-scroll'
export default{
  name: 'CityList',
  props: {
    hot: Array,
    city: Object
  },
  mounted () {
    this.scroll = new BScroll(this.$refs.wrapper)
  }
}
</script>
<style lang="stylus" scoped>
@import '~styles/varibles.styl'
.title
  line-height .54rem
  background #eee
  padding-left .2rem
  color #666
.list
  position absolute
  top 1.58rem
  left 0
  right 0
  bottom 0
  overflow hidden
.border-topbottom
  &:before
    border-color #ccc
  &:after
    border-color #ccc
.border-bottom
  &:before
    border-color #ccc
  &:after
    border-color #ccc
.button-list
  padding .1rem .6rem .1rem .1rem
  overflow hidden
.button-wrapper
  width 33.33%
  float left
.button
  text-align center
  margin .1rem
  border .02rem solid #ccc
  padding .1rem 0
  border-radius .06rem
.item-list
  .item
    line-height .76rem
    padding-left .2rem
</style>
