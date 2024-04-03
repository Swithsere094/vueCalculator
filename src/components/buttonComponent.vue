<template>
    <main v-on:click="this.type == 2 ? $emit('actions', {'selectedValue' : this.buttonValue}) : $emit('click', {'selectedValue' : this.buttonValue})" class="size" :class="backs[this.type]">
        {{ this.buttonValue }}
    </main>
</template>

<script>
    export default {
        props: {
            buttonValue: String,
            type: String,
        },
        name: "buttonComponent",
        setup(){
            const backs = {
                "0": 'back1',
                "1": 'back2',
                "2": 'back3',
            }
            return {
                backs,
            }
        }
    }
</script>

<style scoped>
    main {
        margin: 1vw .2vw 0;
        border-radius: 30px;
        border: 3px inset rgba(160, 167, 184, .2);
        color: #fff;
    }
    .size {
        width: calc(320px/4);
        height: calc(320px/4);
        font-size: x-large;
        user-select: none;
    }
    .back1{
        background: rgb(48,56,67);
        background: radial-gradient(circle, rgba(48,56,67,1) 0%, rgba(42,47,58,1) 40%, rgba(32,36,44,1) 100%);
    }
    .back2{
        background: rgb(100,111,129);
        background: radial-gradient(circle, rgba(100,111,129,1) 0%, rgba(69,82,98,1) 80%, rgba(69,82,98,1) 100%);
    }
    .back3{
        background: rgb(100,111,129);
        background: radial-gradient(circle, rgb(214, 135, 25) 0%, rgb(197, 93, 16) 80%, rgb(197, 93, 16) 100%);
    }
    main:hover {
        background-color: green;
        cursor: pointer;
        border: 3px inset rgba(160, 167, 184, 0);
    }
</style>