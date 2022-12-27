<template>
<Header />
<h1> Hello {{name}}, Welcome to Add Restaurant page</h1>
<form class="add">
    <input type="text" name="name" placeholder="Enter name" v-model="restaurant.resName" />
    <input type="text" name="address" placeholder="Enter address" v-model="restaurant.address" />
    <input type="text" name="contact" placeholder="Enter contact" v-model="restaurant.contact" />
    <button type="button" v-on:click="addNewRestaurant">Add new restaurant</button>
</form>
</template>

<script>
import Header from './Header.vue';
import axios from 'axios';
export default {
    name: "Add",
    data() {
        return {
            name: '',
            restaurant: {
                resName: '',
                address: '',
                contact: ''
            }
        }
    },
    components: {
        Header
    },
    methods: {
        async addNewRestaurant() {
            console.log(this.restaurant)
            const result = await axios.post("http://localhost:3000/restuarants", {
                name: this.restaurant.resName,
                address: this.restaurant.address,
                contact: this.restaurant.contact
            })
            console.warn(result);
            if (result.status == 201) {
                this.$router.push({
                    name: 'Home'
                })
            }
        }

    },
    mounted() {
        let user = localStorage.getItem('user-info');
        this.name = JSON.parse(user)[0].name;
        if (!user) {
            this.$router.push({
                name: 'SignUp'
            })
        }
    }
}
</script>
