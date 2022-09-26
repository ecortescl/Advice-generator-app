<template>
<div role="content" class="bg-home hero is-fullheight">
    <div class="hero-body has-text-centered">
        <div class="container">
            <div class="box">
                <h1>ADVICE #{{result.slip.id}}</h1>
                <h2> {{result.slip.advice}}</h2>

                <div class="columns mt-4">
                    <div class="column ">
                        <img src="images/pattern-divider-desktop.svg">
                    </div>
                </div>

                <div class="columns is-centered">
                    <div class="column is-half">
                        <a @click="getAd()" class="btn-especial">
                            <img src="images/icon-dice.svg">
                        </a>
                    </div>
                </div>

            </div>
        </div>
    </div>
</div>
</template>

<script>
import axios from 'axios'
export default {
    data() {
        return {
            result: ''
        }
    },
    created() {
        this.getAd()
    },
    methods: {

        getAd() {
            axios.get('https://api.adviceslip.com/advice')
                .then(response => {
                    this.result = response.data
                    console.log(this.result)
                })
                .catch(error => {
                    console.log(error)

                })

        }
    }

}
</script>

<style>

.bg-home {
    background: hsl(218, 23%, 16%);
    width: 100%;
    height: 100vh;
}

.box {
    text-align: center;
    border-radius: 10px;
    padding: 20px;
    width: 50%;
    margin: auto;
    background: hsl(217, 19%, 24%)
}

.box h1 {
  font-family: 'Manrope' sans-serif;
    letter-spacing: 0.2em;
    margin-top: 15px;
    margin-bottom: 15px;
    color: hsl(150, 100%, 66%);
    font-weight: bold;
    font-size: 22px;
}

.box h2 {
    font-family: 'Manrope' sans-serif;
   
    color: hsl(193, 38%, 86%);
    font-size: 28px;
    font-weight: bold;
    padding: 5px
}

.btn-especial {
    background: hsl(150, 100%, 66%);
    width: 50px;
    height: 50px;
    -moz-border-radius: 50%;
    -webkit-border-radius: 50%;
    border-radius: 50%;
    position: absolute;
    padding: 15px;
    text-align: center;
    margin-left: -25px;
}

@media (max-width: 1000px) {
    .box {
        width: 100%;
    }

}

@media (max-width: 800px) {
    .box {
        width: 100%;
    }

}
</style>
