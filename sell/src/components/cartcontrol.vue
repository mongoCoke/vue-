<template>
    <div id="cart-control">
        <span class="decrease icon-remove_circle_outline" v-show="food.count > 0" @click="remove"></span>
        <span class="count" v-show="food.count > 0">{{food.count}}</span>
        <span class="increase icon-add_circle" @click="add"></span>
    </div>
</template>
<script>
import Vue from 'vue'
export default {
    props : {
        food : {
            type : Object
        }
    },
    methods : {
        //绑定了一个bsscrol
        add(event){
            if (event._constructed){
                if (!this.food.count){
                    Vue.set(this.food,"count")
                    this.food.count = 1
                }else{
                    this.food.count ++
                }
            }
        },
        remove(){
            if (event._constructed){
                if (this.food.count === 0){
                    return 
                }else{
                    this.food.count --
                }
            }
        }
    }
}
</script>

<style lang="stylus" ref="stylesheet/stylus">
@import '../assets/stylus/index.styl'
#cart-control
    font-size 0
    .icon-remove_circle_outline,.icon-add_circle
        display inline-block
        width 24px
        font-size 24px
        height 24px
        line-height 24px
    .decrease,.increase
        padding 6px
        display inline-block
        line-height 24px
        color #00a0dc        
    .count 
        display inline-block
        width 12px
        text-align center
        font-size 10px        
        color rgb(147,153,159)
        line-height 24px
        padding-top 6px
        vertical-align top
</style>
