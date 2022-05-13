<template>

<section class="bg-image hero__height">
    <div class="container">
        <div class="row">
            <div class="col-xxl-6 col-xl-6 col-lg-6 col-md-8 col-sm-8">
                <div class="hero__content">
                    <h2 class="hero__title">
                        <span class="fw-300" @mouseenter="onMounseEnterEvt" @mouseleave="onMouseLeaveEvt">Happy Birthday, Samieeee 🥳</span> 
                        <br>
                        <button class="btn btn-dark" @click="onBtnClick()">Click me 🎁</button>

                    </h2>

                </div>

            </div>
            <div  class="col-xxl-6 col-xl-6 col-lg-6 col-md-8 col-sm-8">
                <img class="monkey" src="../assets/monkey.png">
                <img class="zebra" src="../assets/zebra.png">
                <img class="elephant" src="../assets/elephant.png">
            </div>              
        </div>
    </div>
    <img src="../assets/banner.png" alt="" class="banner">
    <!-- <button class="btn btn-primary" @click="playSong">play</button> -->
    
</section>
            
            
        
        
</template>
<script>
    const song = require('@/assets/song.mp3')
    export default {
        data: () => ({
            isSongPlaying  : false
        }),
        methods: {
            startConfetti() {
                this.$confetti.start();
                this.$confetti.update({
                    particles: [
                        {
                            type: 'heart',
                        },
                        {
                            type: 'circle',
                        },
                    ],
                    defaultColors: [
                        'red',
                        'pink',
                        '#ba0000'
                    ],
                });
            },

            stopConfetti() {
                this.$confetti.stop();
            },

            onMouseLeaveEvt() {
                this.stopConfetti()
            },

            onMounseEnterEvt() {
                // this.startConfetti()
            },
            playSong() {
                // this.startConfetti()
                let audio = new Audio( song )
    
                audio.autoplay = true
                audio.play().then( response => {
                    console.log( response )
                }).catch( error => {
                    console.log( error )
                })

            },

            onBtnClick() {
                this.startConfetti();
                if( !this.isSongPlaying ) {
                    this.playSong()
                    this.isSongPlaying = true
                }

            }


        },

        mounted() {

}
    }

</script>
<style scoped>

    .banner {
        position: relative;
        width: 500px;
        height: 380px;
        left: 37px;
        transform: rotate(90deg);
        
    }

    .bg-image{
        background-image: url('../assets/bg.png');
        background-size: 1536px 713px;
        background-repeat: no-repeat;
    }

    img.monkey {
        animation: monkeyMove 5s infinite;
        position: absolute;
        
        width: 250px;
        left: 725px;
        top: -100px;
    }

    img.zebra {
        animation: zebraMove 4s infinite;
        position: relative;
        height: 450px;
        width: 300px;
        bottom: -261px;
        left: 445px;
    }

    img.elephant {
        animation: elephantMove 4s infinite;
        position: relative;
        height: 500px;
        width: 400px;
        bottom: 237px;
        margin-left: 60px;
        /* left: 442px; */
    }

    
    @keyframes monkeyMove {
        0%   {top: -10px;}
        25%  {top: 50px;}
        75%  {top: 12px}
        100% {top: 25px;}
    }
    @keyframes zebraMove {
        0%   {left: 445px;}
        25%  {left: 425px;}
        75%  {left: 435px}
        100% {left: 445px;}
    }

     @keyframes elephantMove {
        0%   {left: 0px;}
        25%  {left: 15px;}
        75%  {left: 3px}
        100% {left: 7px;}

    }


    .hero__height {
        min-height: 870px;
        height: 1000px;
    }
    

    .hero__content {
        position: relative;
        z-index: 1;   
    }

    .hero__content p {
        padding-right: 100px;
        margin-bottom: 40px;
        font-size: 16px;
    }

    .hero__title {
        font-size: 60px;
        font-weight: 800;
        margin-top: 250px;
        margin-bottom: 17px;
    }

    .fw-300 {
        font-family: 'Chelsea Market', cursive;
        font-weight: 300;
    }

    .ml-20 {
        margin-left: 20px
    }
</style>