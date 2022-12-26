<template>
<!--<h1>UserName : {{userName}}</h1>
<User :getUserName="getUserName" /><br/><br/>
<input type="text" ref="input" />&nbsp;
<button v-on:click="getData()">Click Me</button>-->
<Child>
    <template v-slot:header>
        <h1>Sowmya</h1>
    </template>
    <template v-slot:main>
        <p>Code step by step</p>
    </template>
    <template v-slot:footer>
        <h6>Copy rights...</h6>
    </template>
</child>
</template>

<script>
import User from './User.vue'
import Child from './Child.vue'
export default {
    name: "HomeComp",
    components: {
        User,
        Child
    },
    data() {
        return {

            userName: ""

        }
    },
    methods: {
        getUserName(name) {
            this.userName = name;
        },
        getData() {
            this.$refs.input.focus();
            this.$refs.input.value = "Sowmya";
            this.$refs.input.style.color = "blue";
        }
    }
}
</script>

<style scoped>
h1 {
    color: orange
}
</style>
