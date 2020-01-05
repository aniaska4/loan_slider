<template lang="pug">
    .main
        .title
            | Hello Ania
        button(@click="click")
</template>
<script>
import loan from "@/assets/json/loan.json"

export default {
    data() {
        return {

        }
    },
    methods: {
        click() {
            console.log(loan.data)
        }
    }
    
}
</script>

<style>

</style>

