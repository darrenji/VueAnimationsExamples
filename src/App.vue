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
    
    @keyframes bounce {
        0% {
            transform: scale(0);
        }
        80% {
            transform: scale(1.2);
        }
        100% {
            transform: scale(1);
        }
    }
    
    .bounce-enter-active {
        animation: bounce .5s;
    }
    
    .bounce-leave-active {
        animation: bounce .5s reverse;
    }
    
    h1 {
        display: inline-block;
    }
</style>
