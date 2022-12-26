<template>
<img alt="Vue logo" src="./assets/logo.png">
<HelloWorld msg="Welcome to Your Vue.js App" />
<HomeComp />
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import HomeComp from './components/HomeComp.vue'

export default {
    name: 'App',
    components: {
        HelloWorld,
        HomeComp
    }
}
</script>
