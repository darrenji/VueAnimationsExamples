<template>
  <div class="container">
      <div class="row">
          <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
           

            
          </div>
      </div>
  </div>
</template>

<script>

    import Child from './Child.vue';
    export default {
        data(){
            return {
                message: 'This is a good place to type things.',
                load: false
            }
        },
        components: {
            appChild: Child
        },
        methods: {
            beforeEnter(el){
                
            }
        }
    }
</script>

<style>
    img {
        width: 100%;
        transform-origin: 50% 50%;
        cursor: pointer;
        transform: scaleY(1) translateZ(0);
        margin: 5px;
    }
    
    main {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
    }
   
</style>
