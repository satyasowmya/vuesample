<template>
<button @click="tab='Java'">Load Java</button>
<button @click="tab='Php'">Load Php</button>
<button @click="tab='Node'">Load Node</button>
<component :is="tab" />
</template>

<script>
import Java from './Java.vue'
import Php from './Php.vue'
import Node from './Node.vue'
export default {
    name: 'HelloWorld',
    components: {
        Java,
        Php,
        Node
    },
    data(){
      return{
      tab: "Java"
      }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>
h3 {
    margin: 40px 0 0;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    display: inline-block;
    margin: 0 10px;
}

a {
    color: #42b983;
}
</style>
