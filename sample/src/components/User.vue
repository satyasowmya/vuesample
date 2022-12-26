<template>
<button v-on:click="getUserName(name)">User Name</button>
</template>

<script>
export default {
    name: 'User',
    data() {
        return {
            name: "Jyothi"
        }
    },
    props: {
        getUserName: Function
    }
}
</script>
