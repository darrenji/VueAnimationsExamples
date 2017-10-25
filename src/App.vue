<template>
  <div class="container">
      <div class="row">
          <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
              <h1>Animations</h1>
              <select v-mode="alertAnimation" class="form-control">
                  <option value="fade">Fade</option>
                  <option value="slide">Slide</option>
              </select>
              <hr>
              <button class="btn btn-primary" @click="show = !show">Show Alert</button>
              <br>
              <br>
              <transition :name="alertAnimation">
<!--                 一个transition内只能包含一个元素-->
                  <div class="alert alert-info" v-show="show">This is some Info</div>
              </transition>
              <transition :name="alertAnimation" type="animation" appear>
<!--                 一个transition内只能包含一个元素-->
                  <div class="alert alert-info" v-if="show">This is some Info</div>
              </transition>
              <transition
                  enter-active-class="animated bounce"
                  leave-active-class="animated shake">
<!--                 一个transition内只能包含一个元素-->
                  <div class="alert alert-info" v-if="show">This is some Info</div>
              </transition>
              
              <transition :name="alertAnimation" mode="out-in">
                  <div class="alert alert-info" v-if="show" key="info">This is some Info bottom</div>
                  <div class="alert alert-warning" v-else key="warning">This is warning</div>
              </transition>
          </div>
      </div>
  </div>
</template>

<script>
    export default {
        data(){
            return {
                show: true,
                alertAnimation: 'fade'
            }
        }
    }
</script>

<style>
    .fade-enter {
        opacity: 0;
    }
    
    .fade-enter-active {
        transition: opacity 1s;
    }
    
    .fade-leave {
        
    }
    
    .fade-leave-active {
        transition: opacity 1s;
        opacity: 0;
    }
    
    .slide-enter {
        
/*
        下面设置过了就不需要设置了
        transform: translateY(20px);
*/
        opacity: 0;
    }
    
    .slide-enter-active {
        animation: slide-in 1s ease-out forwards;
        transition:  opacity .5s;
    }
    
    .slide-leave {
        
    }
    
    .slide-leave-active {
        animation: slide-out 1s ease-out forwards;
        transition: opacity 1s;
        opacity: 0;
    }
    
    @keyframes slide-in {
        from {
            transform: translateY(20px);
        }
        
        to {
            transform: translateY(0);
        }
    }
    
    @keyframes slide-out {
        from {
            transform: translateY(0);
        }
        
        to {
            transform: translateY(20px);
        }
    }
</style>
