<template>
    <main>
        <div class="input">
            <inputComponent :expressionValue="expressionValue" :expression="expression ?? 'Error'"/>
        </div>
        <div class="fila">
            <buttonComponent v-on:actions="actionsClick($event)" type="2" buttonValue="AC"></buttonComponent>
            <buttonComponent v-on:actions="actionsClick($event)" type="2" buttonValue="C"></buttonComponent>
            <buttonComponent v-on:click="clickButton($event)" type="1" buttonValue="("></buttonComponent>
            <buttonComponent v-on:click="clickButton($event)" type="1" buttonValue=")"></buttonComponent>
        </div>
        <div class="fila">
            <buttonComponent v-on:click="clickButton($event)" type="0" buttonValue="7"></buttonComponent>
            <buttonComponent v-on:click="clickButton($event)" type="0" buttonValue="8"></buttonComponent>
            <buttonComponent v-on:click="clickButton($event)" type="0" buttonValue="9"></buttonComponent>
            <buttonComponent v-on:click="clickButton($event)" type="1" buttonValue="/"></buttonComponent>
        </div>
        <div class="fila">
            <buttonComponent v-on:click="clickButton($event)" type="0" buttonValue="4"></buttonComponent>
            <buttonComponent v-on:click="clickButton($event)" type="0" buttonValue="5"></buttonComponent>
            <buttonComponent v-on:click="clickButton($event)" type="0" buttonValue="6"></buttonComponent>
            <buttonComponent v-on:click="clickButton($event)" type="1" buttonValue="*"></buttonComponent>
        </div>
        <div class="fila">
            <buttonComponent v-on:click="clickButton($event)" type="0" buttonValue="1"></buttonComponent>
            <buttonComponent v-on:click="clickButton($event)" type="0" buttonValue="2"></buttonComponent>
            <buttonComponent v-on:click="clickButton($event)" type="0" buttonValue="3"></buttonComponent>
            <buttonComponent v-on:click="clickButton($event)" type="1" buttonValue="-"></buttonComponent>
        </div>
        <div class="fila">
            <buttonComponent v-on:click="clickButton($event)" type="1" buttonValue="."></buttonComponent>
            <buttonComponent v-on:click="clickButton($event)" type="0" buttonValue="0"></buttonComponent>
            <buttonComponent v-on:actions="actionsClick($event)" type="2" buttonValue="="></buttonComponent>
            <buttonComponent v-on:click="clickButton($event)" type="1" buttonValue="+"></buttonComponent>
        </div>
    </main>
</template>

<script>
    import { ref } from "vue";
    import buttonComponent from "./buttonComponent.vue";
    import inputComponent from "./inputComponent.vue";
    export default{
        components: {
            buttonComponent,
            inputComponent
        },
        name:"calculadoraComponent",
        setup(){
            const expression = ref("");
            const expressionValue = ref(0)
            return{
                expression,
                expressionValue,
            }
        },
        methods: {
            actionsClick(event){
                if(event.selectedValue == '='){
                    this.expression = this.expressionValue.toString();
                }

                if(event.selectedValue == 'AC'){
                    this.expression = "";
                    this.expressionValue = 0;
                }

                if(event.selectedValue == 'C'){
                    if(this.expression.length == 1){
                        return;
                    }
                    const expressionLength = this.expression.length;
                    this.expression = this.expression.substring(0, expressionLength-1);
                    this.calculate();
                }
            },
            clickButton(event){
                this.expression += event.selectedValue ?? '';
                this.calculate();
            },
            calculate(){
                // const especialchar = ".+-*/(";
                // if(!especialchar.includes(this.expression.substring(this.expression.length-1))){
                //     this.expressionValue = eval(this.expression);
                // }

                try {
                    const operation = eval(this.expression);
                    this.expressionValue = operation;
                } catch {
                    return;
                }
            }
        }
    }
</script>

<style scoped>
main {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    background-color: #303843;
    width: 50vw;
}
.fila {
    display: flex;
    justify-content: space-around;
}
</style>