<template>
    <main>
        <input disabled class="expression" type="text" :value="this.expression">
        <input disabled class="valor" type="text" :value="this.expressionValue">
    </main>
</template>

<script>
    // import { ref } from 'vue';

    export default {
        props:{
            expression: String,
            expressionValue: Number,
        },
        name: "inputComponent",
        setup(){
            return {
            }
        }
    }
</script>

<style scoped>
    input {
        width: 25vw;
        height: 10vh;
        text-align: right;
        font-size: 40px;
        border: none;
        border-radius: 15px;
        color: #fff;
        background-color: rgba(0, 0, 0, 0);
    }
    .expression {
        font-size: 30px;
        color: rgba(153, 153, 153, 0.3);
    }
</style>