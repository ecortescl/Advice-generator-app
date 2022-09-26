<template>
<div class="">
    {{arrayData}}
</div>
</template>

<script>
import axios from 'axios'
export default {
    data() {
        return {
            arrayData: []
        }
    },
    created() {
        this.getAd()
    },
    methods: {

        getAd() {
            axios.get('https://api.adviceslip.com/advice')
                .then(response => {
                    this.arrayData = response.data.slip.advice
                    console.log(this.arrayData)
                })
                .catch(error => {
                    console.log(error)

                })

        }
    }
}
</script>

<style>

</style>
