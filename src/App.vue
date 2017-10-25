<template>
  <div class="container">
      <div class="row">
          <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
           
            <h3>Hover us</h3>
            <main>
                <app-child>
                <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/28963/cartoonvideo2.jpg" alt="">
                </app-child>
                <app-child>
                    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/28963/cartoonvideo13.jpg" alt="">
                </app-child>
                <app-child>
                    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/28963/cartoonvideo14.jpeg" alt="">
                </app-child>
                <app-child>
                    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/28963/cartoonvideo5.jpg" alt="">
                </app-child>
            </main>
            
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
