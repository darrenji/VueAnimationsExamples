<template>
  <div class="container">
      <div class="row">
          <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
           
            <button @click="show = !show">Toggle Visibility</button><br>
            
            <transition name="bounce">
                <h1 v-show="show">{{text}}</h1>
            </transition>
            
          </div>
      </div>
  </div>
</template>

<script>

    export default {
        data(){
            return {
                text: 'Hello World',
                show: false
            }
        }
    }
</script>

<style>
    
/*
    enter, enter-active, enter-to
    leave, leave-active, leave-to
    如果我们想针对transform做transition效果的话，那enter-active使用ease-out, leave-active使用ease-in
*/
    
    .bounce-enter-active, .bounce-leave-active {
        transition: all .5s;
    }
    
/*    
    enter和leave-to是开始和离开的节点
    enter的时候是绑定，leave-to的时候是解绑
    为什么不在enter-to上设置opacity:1呢？为什么不在leave上设置opacity:1内？因为每个过程节点上的opactiy的默认值就是1
*/
    
    .bounce-enter, .bounce-leave-to {
        transform: scale(0);
    }
    
    h1 {
        display: inline-block;
    }
</style>
