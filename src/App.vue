<template>
  <div class="container">
      <div class="row">
          <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
           
              <hr>
              <div v-bind:class="[show ? blurClass : '',bkClass]">
                  <h3>Trigger modal here</h3>
                  <button @click="toggleShow">
                      <span v-if="show">Hide Child</span>
                      <span v-else>Show Child</span>
                  </button>
              </div>
              
              <transition name="fade">
                 <app-child v-if="show" class="modal1">
                      <button @click="toggleShow">Close</button>
                  </app-child>               
              </transition>

          </div>
      </div>
  </div>
</template>

<script>
    import Child from './Child.vue';
    export default {
        data(){
            return {
                show: false,
                alertAnimation: 'fade',
                bkClass: 'bk',
                blurClass: 'blur'
            }
        },
        methods: {
            toggleShow(){
                this.show = !this.show;
            }
        },
        components: {
            appChild: Child
        }
    }
</script>

<style>
    
/*
    enter, enter-active, enter-to
    leave, leave-active, leave-to
    如果我们想针对transform做transition效果的话，那enter-active使用ease-out, leave-active使用ease-in
*/
    
    .fade-enter-active, .fade-leave-active {
        transition: opacity 0.25s ease-out;
    }
    
/*    
    enter和leave-to是开始和离开的节点
    enter的时候是绑定，leave-to的时候是解绑
    为什么不在enter-to上设置opacity:1呢？为什么不在leave上设置opacity:1内？因为每个过程节点上的opactiy的默认值就是1
*/
    
    .fade-enter, .fade-leave-to {
        opacity: 0;
    }
    
    .bk {
        transition: all 0.1s ease-out;
    }
    
    .blur {
        filter: blur(2px);
        opacity: 0.4;
    }
</style>
