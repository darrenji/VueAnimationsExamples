<template>
  <div class="container">
      <div class="row">
          <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
           
          <h3>Bounce the Ball</h3>
           <button @click="toggleShow">
               <span v-if="isShowing">开始</span>
               <span v-else>让球滚动</span>
           </button>
           
           <transition 
              name="ballmove"
              enter-active-class="bouncein"
              leave-active-class="rollout">
               <div v-if="isShowing">
                   <app-child class="child"></app-child>
               </div>
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
                isShowing: false
            }
        },
        components: {
            appChild: Child
        },
        methods: {
            toggleShow(){
                this.isShowing = !this.isShowing;
            }
        }
    }
</script>

<style>
    
    @keyframes bouncein {
        1% {
            transform: translate3d(0, -400px, 0);
        }
        20%, 40%, 60%, 80%, 95%, 99%, 100% {
            transform: translate3d(0, 0, 0);
        }
        30% {
            transform: translate3d(0, -80px, 0);
        }
        50% {
            transform: translate3d(0, -40px, 0);
        }
        70% {
            transform: translate3d(0, -30px, 0);
        }
        90% {
            transform: translate3d(0, -15px, 0);
        }
        97% {
            transform: translate3d(0, -10px, 0);
        }
    }
    
    .bouncein {
        animation: bouncein 0.8s cubic-bezier(0.25, 0.46, 0.45, 0.94) both;
    }

    .ballmove-enter {
        transform: translate3d(0, -400px, 0);
    }
    
    @keyframes rollout {
        0% {
            transform: translate3d(0, 300px, 0);
        }
        100% {
            transform: translate3d(1000px, 300px, 0);
        }
    }
    
    @keyframes ballroll {
        0% {
            transform: rotate(0);
        }
        100% {
            transform: rotate(1000deg);
        }
    }
    
    .rollout {
        width: 60px;
        height: 60px;
        animation: rollout 2s cubic-bezier(0.55, 0.085, 0.68, 0.53) both;
    }
    
    .rollout div {
        animation: ballroll 2s cubic-bezier(0.55, 0.085, 0.68, 0.53) both;
    }
</style>
