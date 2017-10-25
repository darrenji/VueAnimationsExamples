<template>
    <div class="img-contain">
        <div class="overlay">
            <p class="overlay-text">I dont like this one</p>
            <button @click="toggleShow">Replace</button>
        </div>
        
        <transition name="flip" mode="out-in">
            <slot v-if="!isShowing"></slot>
            <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/28963/cartoonvideo14.jpeg" v-else alt="">
        </transition>
    </div>
</template>

<script>
    export default {
        data(){
            return {
                
            }
        }, 
        props: ['isShowing'],
        methods: {
            toggleShow(){
                this.isShowing = !this.isShowing;
            }
        }
    }
</script>


<style>
    .img-contain {
        width: 250px;
        height: 160px;
        overflow: hidden;
    }
    
    .img-contain .overlay {
        position: absolute;
        z-index: 1000;
        display: block;
        width: 245px;
        height: 155px;
        margin: 5px;
        opacity: 0;
        overflow: hidden;
        transition: 0.3s opacity ease-in;
    }
    
    .img-contain:hover .overlay {
        opacity: 1;
        background: hsla(50, 0%, 0%, 0.6);
        transition: 0.3s opacity ease-out;
    }

</style>