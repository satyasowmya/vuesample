<template>
<Header />
<h1> Hello {{name}}, Welcome to Home page</h1>
<table border="1">
    <thead>
        <td>Id</td>
        <td>Name</td>
        <td>Contact</td>
        <td>Address</td>
        <td>Action</td>
    </thead>
    <tr v-for="item in restaurant" :key="item.id">
        <td>{{item.id}}</td>
        <td>{{item.name}}</td>
        <td>{{item.contact}}</td>
        <td>{{item.address}}</td>
        <td>
            <router-link :to="'/update/'+item.id ">Update</router-link>
            <button v-on:click="deleteRestaurant(item.id)">Delete</button>
        </td>
    </tr>
</table>
</template>

<script>
import Header from './Header.vue'
import axios from 'axios'
export default {
    name: "Home",
    data() {
        return {
            name: '',
            restaurant: []
        }
    },
    components: {
        Header
    },
    methods: {
        async deleteRestaurant(id) {
            let result = await axios.delete("http://localhost:3000/restuarants/" + id)
            console.warn(result);
            if (result.status == 200) {
                this.loadData();
            }
        },
        async loadData() {
            let user = localStorage.getItem('user-info');
            //console.log(JSON.parse(user)[0].name)
            this.name = JSON.parse(user)[0].name;
            if (!user) {
                this.$router.push({
                    name: 'SignUp'
                })
            }
            let result = await axios.get("http://localhost:3000/restuarants")
            console.warn(result);
            this.restaurant = result.data;
        }
    },
    mounted() {
        this.loadData();
    }
}
</script>

<style>
table {
    margin-left: 350px;
}

td {
    width: 160px;
    height: 40px;
}
</style>
